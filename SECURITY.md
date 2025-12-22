# Security Information

## Admin Dashboard Password

The admin dashboard requires a password to access. The password is stored as a SHA-256 hash in `admin.js`.

### Setting Your Password

1. **Generate a strong password** - Use a password manager or create a complex password with:
   - At least 12 characters
   - Mix of uppercase and lowercase letters
   - Numbers
   - Special characters (!@#$%^&*)

2. **Generate the hash:**
   - Open `generate-password-hash.html` in your browser
   - Enter your password
   - Copy the generated hash

3. **Update admin.js:**
   - Open `admin.js`
   - Find `this.PASSWORD_HASH = '...'`
   - Replace with your generated hash
   - Save the file

### Security Best Practices

- **Never commit passwords to version control**
- **Change the default password immediately**
- **Use a unique password for this dashboard**
- **Don't share the password with unauthorized users**
- **Consider using environment variables or server-side authentication for production**

### Current Security Features

- Password is hashed using SHA-256
- Session-based authentication (2-hour timeout)
- Password hash stored client-side (consider server-side for production)
- No password transmitted over network (all client-side)

### For Production

For a production environment, consider:
- Server-side authentication
- HTTPS only
- Rate limiting on login attempts
- Two-factor authentication
- IP whitelisting
- Audit logging

