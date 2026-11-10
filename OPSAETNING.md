# Tvillingesøvn – fælles synkronisering

## 1. Firebase (gratis Spark-plan)
1. Gå til https://console.firebase.google.com/ og opret et projekt. Du behøver ikke aktivere Analytics.
2. I **Build > Authentication > Sign-in method**: aktiver **Email/Password**.
3. I **Build > Firestore Database**: opret en database (vælg en europæisk region, hvis muligt). Vælg **Production mode**.
4. I Firestore > **Rules**: erstat reglerne med indholdet af `firestore.rules`, og tryk **Publish**. Reglerne sikrer, at kun den indloggede familiekonto kan læse og skrive dens data.
5. I **Project settings > General > Your apps**: registrér en **Web app** (`</>`). Du behøver IKKE Firebase Hosting. Kopiér `firebaseConfig`-værdierne til `firebase-config.js` (behold `export const firebaseConfig =`).
6. I **Authentication > Settings > Authorized domains**: tilføj `DITBRUGERNAVN.github.io` hvis det ikke allerede står der.

## 2. GitHub Pages
1. Opret et **Public** repository, fx `tvillingesoevn`.
2. Upload **indholdet** af denne mappe, ikke ZIP-filen. `index.html` skal ligge i roden.
3. I **Settings > Pages** vælg **Deploy from a branch**, **main**, **/(root)** og Save.
4. Åbn `https://DITBRUGERNAVN.github.io/tvillingesoevn/` når deployment er færdig.
5. Tryk **Opret familiekonto** på den første telefon. Log ind med **samme konto** på den anden telefon.
6. På Android Chrome: menu (⋮) > **Føj til startskærm** / **Installer app**.

## Vigtigt
- Firebase-konfigurationen er offentlig i webappen. Det er normalt. Sikkerheden ligger i Authentication og Firestore-reglerne.
- Brug en unik, stærk adgangskode. I deler denne ene konto. Firebase-kontoen kan ikke bruges med hver sin private adgangskode i denne version.
- Der kræves internet til første login. Efter første login kan Firestore cache registreringer og køe ændringer offline, som synkroniseres, når forbindelsen er tilbage.
- Hvis I tidligere brugte den lokale version: Eksportér en backup dér og indlæs den i den nye version.
- Ingen babydata skal uploades til GitHub; kun appfilerne.
- Undgå at bruge en anonym offentlig testdatabase eller regler som `allow read, write: if true`.
- Hvis I redigerer den samme søvnperiode samtidig, kan den sidst synkroniserede ændring vinde.


## Version 2.1
Viser samlet vågentid i dag (tid siden midnat minus registreret søvn), for begge børn. Bevarer Firebase-data. Opdater alle filer på GitHub og tag en backup inden opdateringen.
