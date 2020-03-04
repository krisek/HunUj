A Sword Bibliaolvasó platform egy nyílt forráskódú szoftver, amely különböző bibliafordítások és teológiai művek olvasását teszi lehetővé mindenféle PC-s és mobil platformon (Windows, Linux, Mac, Android, iOS, web). A Sword-re épülő különféle bibliaolvasó alkalmazások többféle felhasználást tesznek lehetővé: a tudományos összehasonlító forráselemzéstől a napi bibliaolvasásig.

Ez a tároló a Magyar Újfordítású Biblia 1990-ben kiadott változatät tartalmazza Osis formátumban, amelyből az alábbi shell szkripttel egyszerűen Sword modul készíthető.

```bash
#prepare location
echo -n "Modulkönyvtár inicializálása..."
git clone https://github.com/krisek/HunUj
cd HunUj
mkdir -p hunuj/modules/texts/ztext/hunuj
mkdir -p hunuj/mods.d
cp -a mods.d hunuj/
cp  hunuj.osis.xml hunuj/modules/texts/ztext/hunuj/
echo "ok."

#generate module
echo -n "Modulkönyvtár generálása..."
osis2mod  hunuj/modules/texts/ztext/hunuj hunuj.osis.xml -v German -z 2>/dev/null
if [ -e hunuj/modules/texts/ztext/hunuj/ot.bzz ]
then
        echo "ok."
else
        echo " "
fi

#package
echo -n "Modulkönyvtár csomagolása..."
cd hunuj
7z a ../hunuj.zip .
cd ..
echo "ok."
```

Amennyiben a ´locales.d` könytárat a $HOME/.sword könyvtárba másolod, magyar könyvcímeket is használhatsz a bibiliaolvasó alkalmazásokban.

A szöveg eredetileg a parokia.hu oldalról származik, ahol már nem hozzáférhető.

A Magyar Biblia Társulat engedélyt adott a Crosswire Bible Society-nek a kész modul terjesztésére, ha Te is terjeszteni akarod, akkor mindeképpen kérd a Magyar Bibliatársulat hozzájárulását.

