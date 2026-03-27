Flask Auth App 

Backend Python-applikasjon med autentisering og rollebaserte tillatelser.

⸻

1. Prosjektbeskrivelse

Dette prosjektet er en webapplikasjon laget med Flask som håndterer:
	•	Brukerregistrering og innlogging
	•	Autentisering
	•	Rollebasert tilgangskontroll (admin, user, guest)
	•	Sesjonsbasert innlogging

Applikasjonen kjører lokalt på egen maskin og er ikke publisert på internett.

⸻

2. Kom i gang

1. Installer Flask
   pip install flask

2. Kjør applikasjonen

Naviger til prosjektmappen i terminalen og kjør:
python app.py

3. Åpne i nettleseren
   
Gå til:
http://127.0.0.1:5001

Hvis alt fungerer, vil du se innloggingssiden i nettleseren.

⸻

3. Prosjektstruktur
flask_auth_app/
├── app.py                  # Hovedapplikasjon (routes, autentisering)
├── notater.json            # Lagring av notater
├── users.json              # Lagring av brukere
├── README.md               # Dokumentasjon
├── requirements.txt        # Avhengigheter
├── static/
│   └── style.css           # CSS (styling)
└── templates/
    ├── base.html           # Felles layout (nav, styling)
    ├── login.html          # Innloggingsside
    ├── dashboard.html      # Hovedside for innloggede brukere
    ├── admin.html          # Admin-panel
    └── user_panel.html     # Brukerpanel

⸻

4. Slik fungerer systemet

Autentisering
	•	Brukere logger inn med brukernavn og passord
	•	Passord hashes ved lagring (SHA-256 brukes i dette prosjektet)
	•	Innloggingsstatus lagres i en Flask session (cookies på serversiden)
	•	Ved utlogging slettes session

Rollebasert tilgang

Tilgang styres basert på brukerrolle:
	•	admin
	•	Full tilgang til alle sider
	•	Kan administrere brukere
	•	user
	•	Tilgang til dashboard og brukerpanel
	•	guest
	•	Begrenset tilgang (kun visning av dashboard)

Tilgang kontrolleres med dekoratorer:
    @login_required
    @role_required('admin')

Disse sørger for at kun autoriserte brukere får tilgang til bestemte sider.

Legge til ny bruker

Brukere legges til i app.py i USERS-dictionary:
    'nybruker': {
    'password': hash_password('passord123'),
    'role': 'user',
    'name': 'Ny Bruker'
}

⸻

5. Teknologier brukt
	•	Python – programmeringsspråk
	•	Flask – web framework
	•	Jinja2 – templating (HTML-generering)
	•	HTML/CSS – frontend
	•	Sessions (cookies) – autentisering og innloggingsstatus

Ingen ekstern database brukes i dette prosjektet; data lagres i minnet i applikasjonen.

⸻

6. Sikkerhet
	•	Passord lagres ved hashing (ikke i klartekst)
	•	Tilgang til sider er beskyttet med rollebasert autentisering
	•	Sessions brukes for å håndtere innloggede brukere
	•	Brukere uten riktig rolle blir nektet tilgang til sensitive sider

⸻

7. Bruk
	1.	Start serveren med python app.py
	2.	Gå til http://localhost:5000
	3.	Logg inn med en av demo-kontoene eller opprett en ny bruker (hvis implementert)
	4.	Naviger mellom dashboard, brukerpanel og admin-panel basert på rolle

⸻

8. Mulige forbedringer
	•	Bruke database (SQLite / PostgreSQL) i stedet for in-memory storage
	•	Implementere bcrypt i stedet for SHA-256 for bedre passordsikkerhet
	•	Legge til registreringsside for nye brukere
	•	Forbedre UI/UX
	•	Logging og feilhåndtering
	•	Token-basert autentisering (JWT)

⸻

9. Oppsummering

Dette prosjektet demonstrerer grunnleggende prinsipper innen:
	•	Autentisering
	•	Autorisering (rollebasert tilgang)
	•	Session-håndtering
	•	Strukturering av en Flask-applikasjon

Det er en enkel, men funksjonell backend-løsning for brukerhåndtering med ulike tilgangsnivåer.
