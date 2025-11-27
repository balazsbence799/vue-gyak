# REST + GraphQL Felhasználólekérő – Vue 3 + Vite

Ez a projekt egy gyakorló feladat, amely bemutatja, hogyan lehet **REST** és **GraphQL** API-ból felhasználókat lekérni **Vue 3 + Vite** környezetben.  
A felhasználók adatai (név, e-mail, telefon) megjelennek, miközben a rendszer **betöltésjelző spinner**-t és **progress bart** mutat.

---

## 1. Projekt létrehozása

A projektet az alábbi parancsokkal készítettük el:

```bash
# 1) Új Vite + Vue projekt generálása
npm create vite@latest vue-gyak -- --template vue

# 2) Belépés a projekt mappájába
cd vue-gyak

# 3) Alap függőségek telepítése
npm install

# 4) Axios telepítése HTTP kérésekhez
npm install axios
