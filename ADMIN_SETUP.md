# CircuitX Admin Dashboard Setup

## Password Protection

The admin dashboard is protected with a password hash. **You MUST set your own secure password before using the dashboard.**

### Step 1: Generate Password Hash

**Recommended Method (Easiest):**
1. Open `generate-password-hash.html` in your browser
2. Enter your desired password (use a strong password with letters, numbers, and symbols)
3. Click "Generate Hash"
4. Copy the generated hash

**Alternative Method (Browser Console):**
1. Open your browser's developer console (F12)
2. Run this command (replace `yourpassword` with your desired password):

```javascript
crypto.subtle.digest('SHA-256', new TextEncoder().encode('yourpassword')).then(hash => {
  const hashArray = Array.from(new Uint8Array(hash));
  const hashHex = hashArray.map(b => b.toString(16).padStart(2, '0')).join('');
  console.log('Your password hash:', hashHex);
});
```

### Step 2: Update admin.js

1. Open `admin.js`
2. Find the line: `this.PASSWORD_HASH = 'a8f5f167f44f4964e6c998dee827110c8c5c5e5e5e5e5e5e5e5e5e5e5e5e5';`
3. Replace the hash with your generated hash from Step 1
4. Save the file

**IMPORTANT:** The default hash is a placeholder and will NOT work. You MUST generate your own password hash before using the admin dashboard.

### Password Security Tips

- Use a strong password (at least 12 characters)
- Include uppercase and lowercase letters
- Include numbers and special characters
- Don't use common words or personal information
- Consider using a password manager
- Never share your password or commit it to version control

## Accessing the Dashboard

1. Navigate to `admin.html` in your browser
2. Enter your password
3. You'll stay logged in for 2 hours (session-based)

## Features

### Kit Management
- Add, edit, and delete kits
- Upload cover images via drag-and-drop
- Manage multiple file categories:
  - Media (Videos)
  - Instructions (PDFs)
  - CAD Models (STL, STEP, etc.)
  - Source Code
  - Tutorial Videos
  - Downloads (Any files)
- Drag and drop files directly into categories
- Edit file paths manually

### Blog Management
- Add, edit, and delete blog posts
- Upload blog images via drag-and-drop
- Edit title, content, and image paths

## Saving Changes

### Option 1: Export JSON Files
1. Click "Export Kits JSON" or "Export Blogs JSON"
2. Download the JSON file
3. Replace the existing `kits-config.json` or `blogs-config.json` file

### Option 2: Manual Save (if you have server access)
The "Save Changes" button will attempt to save directly, but requires server-side support.

## Security Notes

- The password is hashed using SHA-256
- Session expires after 2 hours of inactivity
- Password hash is stored in the JavaScript file (client-side)
- For production, consider implementing server-side authentication
- Keep `admin.html` and `admin.js` files secure and don't commit passwords to version control

## File Structure

After uploading files through the dashboard, you'll need to:
1. Export the JSON configuration
2. Manually upload the actual files to the `assets/` directory
3. Ensure file paths in the JSON match the actual file locations

## Troubleshooting

**Can't login?**
- Check that you've updated the password hash correctly
- Clear browser cache and try again
- Check browser console for errors

**Files not uploading?**
- The dashboard currently handles file paths, not actual file uploads
- You'll need to manually upload files to your server
- Update file paths in the dashboard to match your file structure

**JSON export not working?**
- Check browser console for errors
- Ensure you have permission to download files
- Try a different browser

