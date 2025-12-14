# Pizza Posto - Tactile Dining Restaurant

A modern React application for a tactile dining restaurant with table booking, admin management, and real-time features.

## 🚀 Live Demo

Visit the live application: [Pizza Posto Restaurant](https://shanmukhcr7.github.io/pizza-posto-tactile-dining/)

## ✨ Features

### Customer Features
- **Table Booking**: Reserve tables with individual time slot selection
- **User Authentication**: Google Sign-in and email/password authentication
- **Booking History**: View and manage reservations
- **Real-time Availability**: See available time slots dynamically
- **Responsive Design**: Works on desktop and mobile

### Admin Features
- **Dashboard**: Real-time analytics and management
- **Booking Management**: View and manage all reservations
- **Time Slot Management**: Configure available booking times and capacity
- **Menu Management**: Add/edit menu items
- **User Management**: Manage customer accounts
- **Voucher System**: Create and manage discount vouchers

## 🛠️ Tech Stack

- **Frontend**: React 18, TypeScript, Vite
- **Styling**: Tailwind CSS, Framer Motion
- **UI Components**: Radix UI, Lucide React
- **Backend**: Firebase (Authentication, Firestore, Hosting)
- **State Management**: TanStack Query, React Hook Form
- **Routing**: React Router DOM

## 📦 Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Shanmukhcr7/pizza-posto-tactile-dining.git
   cd pizza-posto-tactile-dining
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure Firebase**:
   - Create a Firebase project
   - Enable Authentication (Email/Password, Google)
   - Set up Firestore Database
   - Update Firebase configuration in `src/lib/firebase.ts`

4. **Update Firestore Rules**:
   ```javascript
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       // Time Slots - allow anonymous users to read (for booking)
       match /timeSlots/{slotId} {
         allow read: if true;  // Allow anyone to read time slots for booking
         allow write: if request.auth != null && 
           exists(/databases/$(database)/documents/users/$(request.auth.uid)) &&
           get(/databases/$(database)/documents/users/$(request.auth.uid)).data.role == 'admin';
       }
       
       // Other collections with proper admin permissions...
     }
   }
   ```

## 🚀 Deployment to GitHub Pages

1. **Install gh-pages**:
   ```bash
   npm install --save-dev gh-pages
   ```

2. **Deploy**:
   ```bash
   npm run deploy
   ```

3. **Configure GitHub Pages**:
   - Go to repository Settings → Pages
   - Select "Deploy from a branch" → "gh-pages" branch
   - Save

## 🎯 Usage

### For Customers
1. Visit the website
2. Browse menu and featured pizzas
3. Use the booking panel to reserve a table
4. Sign in to complete booking
5. View booking history in "My Bookings"

### For Admin
1. Visit `/admin/login`
2. Login with admin credentials
3. Access dashboard for management features
4. Configure time slots and manage reservations

## 📱 Key Features Implementation

### Time Slot Management
- **Admin sets time ranges** (e.g., 6:00 PM - 10:00 PM)
- **System generates 30-minute intervals** automatically
- **Customers see individual time choices** (6:00 PM, 6:30 PM, 7:00 PM, etc.)
- **Real-time availability** calculation

### Authentication Flow
- **Google Sign-in** with popup and redirect fallback
- **Email/password** authentication
- **Role-based access** (admin/customer)
- **Protected routes** for admin areas

### Booking System
- **Smart date validation** (tomorrow's date minimum)
- **Real-time slot loading** based on admin configuration
- **Automatic capacity tracking**
- **Booking status management**

## 🔧 Development

### Build Commands
```bash
# Development server
npm run dev

# Production build
npm run build

# Preview production build
npm run preview

# Deploy to GitHub Pages
npm run deploy
```

### Environment Configuration
Update `src/lib/firebase.ts` with your Firebase configuration:
```typescript
const firebaseConfig = {
  apiKey: "your-api-key",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "your-sender-id",
  appId: "your-app-id"
};
```

## 🎨 Customization

### Styling
- Modify `tailwind.config.ts` for custom colors and themes
- Update CSS variables in `src/index.css`
- Customize component styles in individual component files

### Time Slots
- Configure default time slots in `src/lib/seedMenu.ts`
- Adjust booking intervals in `src/pages/BookingForm.tsx`
- Modify availability calculation in `src/lib/slotsService.ts`

## 📄 License

This project is private and proprietary.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📞 Support

For support and questions, please contact the development team.

---

**Pizza Posto** - Where every bite is a journey to Naples 🍕
