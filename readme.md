Absolute Path ile kesin bir yol tanımı yapıp nerede olursak olalım bu kesin yol tanımını kullanarak dosyalarımızı çağırabiliyoruz. 
```javascript
import Header from '../../components/Header'
import HeroSection from '../../components/HeroSection';
import { numberFormat } from '../../../helpers/Mixins';
```
Nihayetinde şöyle kullanmak için:
```javascript
import Header from '~/components/Header'
import HeroSection from '~/components/HeroSection';
import { numberFormat } from '~/helpers/Mixins';
```

Eğer typescript kullanıyorsan tsconfig.json javascript kullanıyorsanız jsconfig.json dosyasını ana dizinde oluştur:

```javascript
{
	"compilerOptions": {
	    "baseUrl": "./src",
	    "paths": {
	      "~/*": ["./*"]
	    }
	}
}
```

ve vite.config.(ts|js) dosyanızı açıp şunu ekle:

```javascript
resolve: {
    alias: {
      '~': path.resolve(__dirname, 'src'),
    },
  },
```

Eğer path bulamazsa en üstte şöyle import et:
```javascript
import * as path from "path"
```
Vite'i yeniden başlat