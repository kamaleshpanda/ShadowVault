I am building a full-stack AI project called:

"AI-Powered Global Threat Intelligence Map with Satellite Damage Assessment"

Project Overview:

- Frontend: Next.js with Mapbox (interactive map UI)
    
- Backend: FastAPI (API + ML inference)
    
- Database: PostgreSQL / SQLite (store events and analysis)
    
- Data Sources:
    
    - ACLED / GDELT (real-world conflict & event data)
        
    - Sentinel-2 (satellite imagery)
        
- AI Components:
    
    - Google Gemini API (event summarization + classification)
        
    - U-Net (satellite image damage segmentation)
        
    - Change detection (before vs after images)
        

Core Features:

1. Live map showing global events (attacks, conflicts, disasters)
    
2. Events stored in database and updated via scheduler (cron job)
    
3. Click event → show:
    
    - AI-generated summary (Gemini)
        
    - Damage percentage (ML model)
        
    - Heatmap overlay (segmentation)
        
    - Before vs After satellite images
        
4. Near real-time updates (not military real-time)
    
5. Optional features:
    
    - Timeline slider
        
    - Alerts system
        
    - Analytics dashboard
        

Architecture:

- Data ingestion → Database → Backend API → Frontend Map
    
- ML runs on-demand when user clicks an event
    
- Scheduler fetches new events periodically
    

Constraints:

- Only free APIs/tools (no paid services like Valyu)
    
- Keep system scalable and modular
    
- Focus on practical implementation, not over-complexity
    

What I need from you:

- Step-by-step implementation guidance
    
- Code snippets (frontend, backend, ML)
    
- Debugging help
    
- Best practices for deployment and optimization
    

Continue guiding me from where I left off.