
# Real-Time Collaborative Document Editor (Task 62)

### 1. Project Architecture
- **Frontend:** React.js (State Management)
- **Backend:** Node.js with Socket.io (Real-time Sync)
- **Database:** MongoDB (JSON-based Document Storage)
- **Editor:** Quill.js Integration

### 2. Implementation Logic (Core Code)
```javascript
import React, { useEffect, useState } from "react";
import Quill from "quill";
import "quill/dist/quill.snow.css";
import { io } from "socket.io-client";

const SAVE_INTERVAL_MS = 2000;
const socket = io("http://localhost:5000");

const TextEditor = ({ documentId }) => {
  const [quill, setQuill] = useState();

  // Initialize Quill Editor
  useEffect(() => {
    const editor = new Quill("#container", { theme: "snow" });
    setQuill(editor);
  }, []);

  // Socket: Send changes to server
  useEffect(() => {
    if (socket == null || quill == null) return;

    const handler = (delta, oldDelta, source) => {
      if (source !== "user") return;
      socket.emit("send-changes", delta);
    };
    quill.on("text-change", handler);

    return () => quill.off("text-change", handler);
  }, [socket, quill]);

  // Socket: Receive changes from other users
  useEffect(() => {
    if (socket == null || quill == null) return;

    const handler = (delta) => {
      quill.updateContents(delta);
    };
    socket.on("receive-changes", handler);

    return () => socket.off("receive-changes", handler);
  }, [socket, quill]);

  return <div id="container" style={{ height: "80vh", background: "#fff" }}></div>;
};

export default TextEditor;
