# Contributing to Dompet Keluarga

Terima kasih atas minat Anda untuk berkontribusi! 🎉

## Code of Conduct

Proyek ini mengadopsi kode etik yang kami harapkan semua kontributor patuhi. Bersikaplah sopan dan menghormati semua orang.

## Cara Berkontribusi

### Melaporkan Bug

Jika Anda menemukan bug:

1. **Check existing issues** - Pastikan bug belum dilaporkan
2. **Create detailed issue** - Sertakan:
   - Deskripsi bug yang jelas
   - Langkah-langkah untuk reproduce
   - Expected behavior vs actual behavior
   - Screenshots jika memungkinkan
   - Browser & OS yang digunakan
   - Console errors (jika ada)

### Mengusulkan Fitur Baru

1. **Check existing issues** - Pastikan fitur belum diusulkan
2. **Create feature request** - Jelaskan:
   - Masalah yang ingin diselesaikan
   - Solusi yang diusulkan
   - Alternatif yang sudah dipertimbangkan
   - Mockup atau wireframe (jika ada)

### Pull Request Process

1. **Fork repository**
```bash
git clone https://github.com/yourusername/dompet-keluarga-pub.git
```

2. **Create feature branch**
```bash
git checkout -b feature/nama-fitur-anda
```

3. **Setup development environment**
```bash
npm install
cp .env.example .env
# Edit .env dengan Firebase config Anda
```

4. **Make your changes**
   - Ikuti code style yang ada
   - Tambahkan comments untuk kode kompleks
   - Update dokumentasi jika diperlukan

5. **Test your changes**
```bash
npm run dev
# Test manual di browser
npm run build
# Pastikan build berhasil
```

6. **Commit changes**
```bash
git add .
git commit -m "feat: deskripsi fitur yang jelas"
```

Gunakan conventional commits:
- `feat:` - Fitur baru
- `fix:` - Bug fix
- `docs:` - Perubahan dokumentasi
- `style:` - Format code (tidak mengubah logic)
- `refactor:` - Refactor code
- `test:` - Tambah atau update tests
- `chore:` - Update dependencies, config, dll

7. **Push to your fork**
```bash
git push origin feature/nama-fitur-anda
```

8. **Create Pull Request**
   - Buka GitHub dan create PR
   - Jelaskan perubahan yang dilakukan
   - Link ke issue terkait (jika ada)
   - Tambahkan screenshots untuk UI changes

## Development Guidelines

### Code Style

- **JavaScript**: Gunakan ES6+ syntax
- **React**: Functional components dengan Hooks
- **Naming**:
  - Components: PascalCase (`TransactionList`)
  - Functions: camelCase (`formatCurrency`)
  - Constants: UPPER_SNAKE_CASE (`FIREBASE_CONFIG`)
- **Indentation**: 2 spaces
- **Quotes**: Single quotes untuk strings
- **Semicolons**: Optional tapi konsisten

### Component Structure

```javascript
// 1. Imports
import React, { useState, useEffect } from 'react';
import { Icon } from 'lucide-react';

// 2. Constants
const DEFAULT_VALUE = 10;

// 3. Helper functions
const helperFunction = () => {};

// 4. Component
const MyComponent = ({ prop1, prop2 }) => {
  // States
  const [state, setState] = useState(null);
  
  // Effects
  useEffect(() => {}, []);
  
  // Handlers
  const handleClick = () => {};
  
  // Render
  return (
    <div></div>
  );
};

// 5. Export
export default MyComponent;
```

### Firebase Best Practices

1. **Security**: Jangan commit credentials
2. **Queries**: Gunakan indexing untuk query kompleks
3. **Real-time**: Cleanup listeners dengan `unsubscribe()`
4. **Error Handling**: Selalu handle errors dari Firebase
5. **Batch Operations**: Gunakan batch untuk multiple writes

### State Management

- Gunakan `useState` untuk local state
- Gunakan `useEffect` untuk side effects
- Gunakan `useMemo` untuk expensive computations
- Gunakan `useCallback` untuk function memoization

### Performance

- Lazy load components jika memungkinkan
- Memoize expensive computations
- Optimize re-renders dengan `React.memo`
- Minimize Firestore reads dengan caching

## Testing

Sebelum submit PR, test:

1. **Manual testing** - Semua fitur berfungsi
2. **Cross-browser** - Test di Chrome, Firefox, Safari
3. **Responsive** - Test di mobile dan desktop
4. **Error cases** - Test error handling
5. **Firebase rules** - Test dengan Rules Simulator

## Documentation

Update dokumentasi jika:

- Menambah fitur baru
- Mengubah behavior existing
- Menambah dependencies baru
- Mengubah setup process

Files yang perlu di-update:
- `README.md` - Overview dan quick start
- `SETUP.md` - Detailed setup instructions
- `CONTRIBUTING.md` - This file
- Code comments - Untuk complex logic

## Questions?

Jika ada pertanyaan:
1. Check [README.md](README.md) dan [SETUP.md](SETUP.md)
2. Search existing issues
3. Create new issue dengan label "question"

## License

Dengan berkontribusi, Anda setuju bahwa kontribusi Anda akan dilisensikan di bawah MIT License yang sama dengan project ini.

---

Terima kasih telah berkontribusi! 💚
