# Lwandeti Junction Minimart - Firebase E-Commerce Website

A complete e-commerce website with real-time cloud database synchronization using Firebase Firestore.

## 🚀 Features

- **Real-time Sync**: Products sync instantly between admin panel and homepage
- **Cloud Database**: Firebase Firestore for reliable data storage
- **Image Upload**: Firebase Storage for product images
- **WhatsApp Integration**: Direct ordering via WhatsApp
- **Responsive Design**: Mobile-friendly interface
- **Admin Dashboard**: Secure product management

## 📁 File Structure

```
/
├── index.html          # Homepage with Firebase sync
├── admin.html          # Admin panel with product management
├── products.json       # Initial product data (for seeding)
└── README.md          # This file
```

## 🔧 Firebase Setup

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project named "Lwandeti Junction Minimart"
3. Enable **Firestore Database** (start in test mode)
4. Enable **Storage** (for product images)
5. Get your configuration credentials (already included in files)

### Security Rules (Firestore)

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read: if true;
      allow write: if request.auth != null || request.time < timestamp.date(2025, 12, 31);
    }
  }
}
```

### Security Rules (Storage)

```javascript
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read: if true;
      allow write: if request.auth != null || request.time < timestamp.date(2025, 12, 31);
    }
  }
}
```

## 🚀 Deployment Options

### Option 1: Netlify (Recommended)
1. Drag and drop all files to [Netlify Drop](https://app.netlify.com/drop)
2. Your site will be live instantly
3. Auto-sync with Firebase works immediately

### Option 2: Firebase Hosting
```bash
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy
```

### Option 3: GitHub Pages
1. Push files to a GitHub repository
2. Enable GitHub Pages in repository settings
3. Site will be live at `username.github.io/repo-name`

## 🔐 Admin Access

- **URL**: `your-site.com/admin.html`
- **Password**: `admin123`
- **Hidden Link**: Bottom-right corner of homepage (invisible dot)

## 📱 How It Works

### Adding Products (Admin)
1. Login to admin panel
2. Fill product form (name, price, category, image)
3. Click "Save Product"
4. Product appears instantly on homepage

### Real-time Updates
- Admin adds/edits/deletes product → Homepage updates automatically
- No page refresh needed
- Works across all connected devices

### Image Handling
- Upload images directly or paste URL
- Images stored in Firebase Storage
- Automatic CDN delivery

## 🛒 Customer Flow

1. Browse products on homepage
2. Add items to cart
3. Click "Order via WhatsApp"
4. Pre-filled WhatsApp message opens
5. Send order to store owner

## 📊 Database Collections

### Products Collection
```javascript
{
  id: string,
  name: string,
  price: number,
  oldPrice: number | null,
  unit: string,
  category: string,
  badge: string,
  description: string,
  popular: boolean,
  inStock: boolean,
  image: string,
  createdAt: timestamp,
  updatedAt: timestamp
}
```

### Categories Collection
```javascript
{
  id: string,
  name: string,
  icon: string,
  color: string,
  image: string,
  defaultProductImage: string
}
```

## 🔧 Customization

### Change Store Info
Edit in `admin.html` and `index.html`:
- Phone: `0117 352700`
- WhatsApp: `254117352700`
- Email: `junctionsupa@gmail.com`

### Change Admin Password
In `admin.html`, find:
```javascript
const ADMIN_PASSWORD = 'admin123';
```

### Add/Edit Categories
Modify the `defaultCategories` array in `admin.html`

## 🐛 Troubleshooting

### "Database not connecting"
- Check Firebase configuration in both files
- Ensure Firestore is enabled in Firebase Console
- Check browser console for errors

### "Images not uploading"
- Verify Firebase Storage is enabled
- Check Storage security rules
- Ensure file size is under 5MB

### "Products not syncing"
- Check internet connection
- Verify Firestore rules allow read/write
- Check browser console for errors

## 📞 Support

For issues or questions:
- WhatsApp: 254117352700
- Email: junctionsupa@gmail.com

## 📝 License

This project is proprietary to Lwandeti Junction Minimart.

---

**Last Updated**: March 2025
**Version**: 2.0 (Firebase Edition)

