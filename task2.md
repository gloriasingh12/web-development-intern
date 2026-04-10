
# Online Learning Platform (Task 61)

### 1. React Implementation (Core UI & Logic)
```javascript
import React, { useState } from 'react';

const LearningPlatform = () => {
    const [progress, setProgress] = useState(0);
    const [lesson, setLesson] = useState("Introduction to React");

    const completeLesson = () => {
        if (progress < 100) setProgress(progress + 25);
        alert("Lesson Completed! Keep it up.");
    };

    return (
        <div style={{ background: '#f8fafc', minHeight: '100vh', padding: '20px', fontFamily: 'Arial' }}>
            {/* Header & Progress Tracking */}
            <div style={{ display: 'flex', justifyContent: 'space-between', padding: '20px', background: '#fff', borderRadius: '10px', boxShadow: '0 2px 10px rgba(0,0,0,0.1)' }}>
                <h2 style={{ color: '#2563eb' }}>SOIT Academy</h2>
                <div style={{ textAlign: 'right' }}>
                    <strong>Progress: {progress}%</strong>
                    <div style={{ width: '200px', background: '#e2e8f0', height: '10px', borderRadius: '5px', marginTop: '5px' }}>
                        <div style={{ width: `${progress}%`, background: '#22c55e', height: '100%', borderRadius: '5px', transition: '0.5s' }}></div>
                    </div>
                </div>
            </div>

            {/* Video Player Section */}
            <div style={{ marginTop: '30px', display: 'grid', gridTemplateColumns: '2fr 1fr', gap: '20px' }}>
                <div style={{ background: '#000', borderRadius: '15px', height: '400px', display: 'flex', alignItems: 'center', justifyContent: 'center', color: '#fff' }}>
                    <h3>📺 [Video Player: {lesson}]</h3>
                </div>

                {/* Course Content */}
                <div style={{ background: '#fff', padding: '20px', borderRadius: '15px' }}>
                    <h3>Course Content</h3>
                    <ul style={{ listStyle: 'none', padding: 0 }}>
                        <li style={listStyle} onClick={() => setLesson("React Basics")}>✅ React Basics</li>
                        <li style={listStyle} onClick={() => setLesson("State & Props")}>✅ State & Props</li>
                        <li style={listStyle} onClick={() => setLesson("Hooks Depth")}>📖 Hooks in Depth</li>
                        <li style={listStyle} onClick={() => setLesson("API Integration")}>📖 API Integration</li>
                    </ul>
                    <button onClick={completeLesson} style={btnStyle}>Mark as Complete</button>
                </div>
            </div>
        </div>
    );
};

const listStyle = { padding: '10px', borderBottom: '1px solid #eee', cursor: 'pointer' };
const btnStyle = { width: '100%', padding: '12px', background: '#2563eb', color: '#fff', border: 'none', borderRadius: '8px', marginTop: '20px', fontWeight: 'bold', cursor: 'pointer' };

export default LearningPlatform;
