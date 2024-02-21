# Backend aufsetzen - die Steps

Projekt anlegen und die Config:
- Order für das Backend anlegen und in VsCode öffnen
- npm init -y
- Modulsystem ändern => einen key "type": "module" einfügen (z.B. unter "licence")
  - dadurch können wir "import ... from ..." in den JS Dateien benutzen
- Packages installieren, die wir Minimum für ein Backend brauchen: npm i express mongoose dotenv cors
- .env Datei im Ordner anlegen
- DB in ATLAS aufsetzen
- wenn schon Daten in JSON File vorhanden: Dateien in DB importieren 
- Connection String / URL aus Compass kopieren
- Connection String / URL in .env kopieren und Variablen-Namen davor schreiben
  - Den Variablen-Namen brauchen wir, um im Code dann an diese URL im Code ranzukommen
  - Beispiel: MONGO_URL=<deinConnectionStringVonCompass>

Verbindung mit Datenbank im Code aufsetzen:
- db-connect.js File anlegen
- Packages dotenv und mongoose importieren
- mit dotenv.config wird die .env Datei eingelesen und alle Inhalte in die spezielle Variable "process.env" geladen
- process.env ist in ALLEN JS Files verfügbar. Somit kommen alle JS Files an die Config heran
- Mit mongoose.connect( process.env.MONGO_URL ) Verbindung herstellen
- mit then() und catch() Handlers checken, ob Verbindung geklappt hat oder gescheitert ist

Backend aufsetzen:
- app.js File anlegen
- Package "express" importieren
- mit express() wird ein brandneues Backend erstellt. Wir speichern es in der Variable "app"
- mit app.listen starten wir das Backend auf einem Port (dadurch kann ein Frontend darauf zugreifen, über den geöffneten Port)
- Wenn das Backend gestartet ist, wird die Function ausgeführt, die wir in app.listen nach dem Port angeben

Routes aufsetzen:
- mit app.get() setzen wir eine RUFNUMMER und den BEARBEITER hinter der Rufnummer auf
- Beispiel: app.get("/", (req, res) => { res.send("halloooo") }
- Der erste Teil "/" ist die ROUTE. Das ist die RUFNUMMER, unter der das Frontend anrufen kann
- Der zweite Teil  (req, res) => { res.send("halloooo") } ist der BEARBEITER, der den Anruf entgegennimmt und antwortet
- res.send() sendet dem Anrufer eine Antwort zurück (=> also meistens DATEN aus der Datenbank)

- 
