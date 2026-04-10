# Advanced Animated Portfolio (Task 60)

### 1. React + GSAP Implementation
```javascript
import React, { useEffect, useRef } from 'react';
import { gsap } from 'gsap';

const Portfolio = () => {
    const headerRef = useRef(null);
    const cardRef = useRef(null);

    useEffect(() => {
        // Entrance Animation
        gsap.from(headerRef.current, { 
            duration: 1.5, 
            y: -100, 
            opacity: 0, 
            ease: 'bounce' 
        });

        // Hover Effect Animation logic
        gsap.from(cardRef.current, { 
            duration: 1, 
            scale: 0.8, 
            opacity: 0, 
            delay: 0.5,
            stagger: 0.2 
        });
    }, []);

    return (
        <div style={{ background: '#0f172a', color: '#fff', minHeight: '100vh', fontFamily: 'Poppins' }}>
            <header ref={headerRef} style={{ textAlign: 'center', padding: '100px 20px' }}>
                <h1 style={{ fontSize: '4rem', color: '#38bdf8' }}>Aditya Tripathi</h1>
                <p style={{ fontSize: '1.5rem' }}>Full Stack Developer & Hardware Designer</p>
            </header>

            <div ref={cardRef} style={{ display: 'flex', justifyContent: 'center', gap: '20px' }}>
                <div style={cardStyle}>Project 1</div>
                <div style={cardStyle}>Project 2</div>
                <div style={cardStyle}>Project 3</div>
            </div>
        </div>
    );
};

const cardStyle = {
    width: '250px',
    height: '350px',
    background: '#1e293b',
    borderRadius: '15px',
    display: 'flex',
    alignItems: 'center',
    justifyContent: 'center',
    border: '1px solid #334155',
    fontSize: '1.2rem'
};

export default Portfolio;
