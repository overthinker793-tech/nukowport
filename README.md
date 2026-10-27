# portfolio-cicd

Қазақ тіліндегі студент портфолиосы және GitHub Actions көмегімен жасалған қарапайым CI тапсырмасы.

## Жоба құрылымы

```text
portfolio-cicd/
├── .github/
│   └── workflows/
│       └── ci.yml
├── index.html
├── style.css
├── .gitignore
└── README.md
```

## Жергілікті компьютерде ашу

1. `index.html` файлын браузерде ашыңыз.
2. Сайттың сыртқы көрінісі `style.css` файлы арқылы беріледі.

## GitHub-қа жіберу

Git және GitHub орнатылғаннан кейін VS Code терминалында осы бумаға кіріп, мына командаларды орындаңыз:

```bash
git init
git add .
git commit -m "Create portfolio"
git branch -M main
```

GitHub-та `portfolio-cicd` атты бос репозиторий құрыңыз. Төмендегі `USERNAME` орнына өз GitHub логиніңізді қойыңыз:

```bash
git remote add origin https://github.com/USERNAME/portfolio-cicd.git
git push -u origin main
```

## CI workflow қалай жұмыс істейді?

`.github/workflows/ci.yml` файлы GitHub Actions процесін сипаттайды. Ол `main` тармағына `push` жасалғанда немесе `main` тармағына бағытталған Pull Request ашылғанда іске қосылады.

Workflow үш негізгі қадамнан тұрады:

1. `actions/checkout@v4` — репозиторий кодын орындау ортасына жүктейді.
2. `test -f index.html` — `index.html` файлының бар екенін тексереді. Файл табылмаса, қадам сәтсіз аяқталады.
3. `echo "Portfolio check passed!"` — тексеру сәтті өтсе, хабарлама шығарады.

Нәтижені GitHub репозиторийіндегі **Actions** бөлімінен қараңыз.

## Қате жағдайын тексеру

1. `index.html` файлын уақытша `home.html` деп өзгертіңіз.
2. Өзгерісті commit жасап, GitHub-қа жіберіңіз.
3. **Actions** бөлімінен `Check index.html` қадамының сәтсіз болғанын тексеріңіз.
4. Файлды қайтадан `index.html` деп атаңыз да, өзгерістерді жіберіңіз.
5. Workflow сәтті аяқталғанын тексеріңіз.

> Бұл оқу тапсырмасы файлдың бар-жоғын тексереді. Ол HTML кодын толық тексермейді және сайтты серверге автоматты жарияламайды.
