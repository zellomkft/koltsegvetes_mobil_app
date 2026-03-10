# Moodboard

- Bevételek
  - honnan, típusok (egyszeri/rendszeres)
  - Csoportosítás (típusok) => családi, részvények stb. csoport

- Kiadások
  - havi/rendszeres/sos -> tipizálás

- Megtakarítás
- Adott bankszámlához kapcsolás
- Kimutatások, előreláthatósági kimutatás (időszakos / heti / havi)
- Álmok / célok / célkítűzések
- Popup / push notifications / triggerek
- Widgetek

- Google API
- Tanácsadó (LLM) -> (MIT NE CSINÁLJ?!) - KÉT KÜLÖN CONTEXT -> Laravel AI kit

---

# Projekt telepítés

## 1. Laravel létrehozása

A projekt root-jába futtasd:

```bash
composer create-project laravel/laravel backend
```

## 2. React Native létrehozása

A projekt root-jába futtasd:

```bash
npx @react-native-community/cli init frontend
```

## 3. Docker image-ek buildelése

```bash
docker-compose build php-fpm react_native
```

## 4. Teljes stack indítása

```bash
docker-compose up -d
```

## 5. Elérés

- Laravel backend: [localhost](http://localhost)
- React Native frontend: [localhost:8081](hhttp://localhost:8081)
