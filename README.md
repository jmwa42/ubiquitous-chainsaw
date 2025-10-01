# whatsapp-gpt-bot

## Data Persistence on Railway

To prevent data loss when your application is rebuilt or restarted on Railway, you need to set up **persistent volumes**. This application stores important data in two directories:

- `bot/`: Contains all the JSON data files for FAQs, fees, user chats, etc.
- `.wwebjs_auth/`: Stores the WhatsApp session data, so you don't have to re-scan the QR code on every deployment.

Follow these steps to configure persistent storage on Railway:

1.  **Go to Your Project:** Open your project on the Railway dashboard.
2.  **Add a Volume:**
    -   Click the "+ New" button.
    -   Select "Volume" from the dropdown menu.
    -   A new volume will be created. You can keep the default name.
3.  **Mount the Volume to Your Service:**
    -   Go to your service's settings (the one running this bot).
    -   Click on the "Volumes" tab.
    -   You will see two fields: "Mount Path" and "Volume".
4.  **Mount the `bot` Directory:**
    -   In the "Mount Path" field, enter `/app/bot`.
    -   In the "Volume" dropdown, select the volume you just created.
    -   Click "Add".
5.  **Mount the WhatsApp Session Directory:**
    -   Click "Add Another Mount Path".
    -   In the new "Mount Path" field, enter `/app/.wwebjs_auth`.
    -   In the "Volume" dropdown, select the same volume.
    -   Click "Add".

After completing these steps, Railway will automatically mount the specified directories to the persistent volume. Your data will now be safe across deployments.

