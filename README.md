# CloakRoom-issue-solution
## **Issue / Problem**
- Multiple users sending messages simultaneously caused messages to be **delivered out of order**, confusing active conversations.  
- Occasionally, messages were **lost**, never appearing for some users.  
- The root cause was **race conditions**, as Socket.IO events fired **before messages were fully stored** in the database.

## **Solution**
- Integrated **Kafka** to queue messages and ensure **ordered delivery**.  
- Modified backend to **store messages first**, then emit via Socket.IO.  
- Added **Redis caching** to serve recent messages quickly and reduce database load.  
- Optimized Socket.IO event handling to **prevent race conditions** during high concurrency.

## **Outcome**
- Messages are now **delivered in correct order** without duplication or loss.  
- Chat history is **consistent for all users** even under heavy load.  
- The application is **stable, low-latency, and reliable** for multiple concurrent users.

