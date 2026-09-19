<p align="center">
  <img src="assets/logo.png" alt="NexusCRM" width="300" />
</p>

# NexusCRM

A CRM for small sales teams — clients, contacts, tasks, and a log of every
interaction in one place.

I built this during a one-month internship at OEM Engineering in Sfax. It was my
first time shipping something end to end: four one-week sprints, tracked in Jira,
from the UML diagrams to a running container.

| Dashboard | Login |
| :---: | :---: |
| ![Dashboard](assets/dashboard.png) | ![Login](assets/login.png) |

## What it does

- Manage clients and their contacts, and keep a shared history of calls, meetings and emails
- Log in with a password, then a one-time code sent to your inbox
- Assign tasks with deadlines between managers and employees
- Get notified when records change
- See activity at a glance on a stats dashboard
- Switch the whole interface between English and French

Access is split three ways — super-admin, admin and employee — and each role only
sees what it should.

**Built with** Django REST Framework, React 19, MySQL, JWT, Docker, deployed on Railway.

The front end started from the [Datta Able](https://github.com/codedthemes/datta-able-free-react-admin-template)
admin template (MIT). The layout and charts come from there; the API, the login flow,
the translations and every CRM screen are mine.

## Running it

You'll need Python 3.11+, Node 18+, and MySQL (optional — it falls back to SQLite).

```bash
git clone https://github.com/salmenhammami/NexusCRM.git

# API
cd NexusCRM/backend
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env          # add your DB and SMTP settings
python manage.py migrate
python manage.py runserver

# Web app, in another terminal
cd ../frontend
cp .env.example .env
npm install
npm start
```

The OTP emails go out over SMTP, so the login won't complete until you fill in the
email settings in `backend/.env`.

## Still to do

Tests, a tighter CORS policy, and a CI workflow. The two-step login is the first
thing I'd write tests for.

---

**Salmen Hammami** · [GitHub](https://github.com/salmenhammami) · [LinkedIn](https://www.linkedin.com/in/salmenhammami/)
