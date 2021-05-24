---
layout: post
title: Jira & Toggl. Jak uspójnić formę raportowania?
image: /assets/20170308_header.jpg
article_language: pl
---

# Projekt i początkowe założenia

Pomysł na realizowany kawałek oprogramowania wywodzi się z tego, że od ponad roku funkcjonuję jako miękka forma inteligencji ([Jak rozmawiać z obcymi formami inteligencji - poradnik dla craftsmanów, Slawomir Sobotka](https://www.youtube.com/watch?v=0XITfxBCYpc&t=7s)), a nie jako programista. W świecie zarządzania projektami (podobnie jak w programistycznym) często zachodzi zjawisko odkrywania koła na nowo lub wykorzystywania nieadekwatnych (lub zbyt wielu) narzędzi do osiągnięcia celów. Narzędzia tworzone w ramach projektu będą miały na celu automatyzację żmudnych czynności wykonywanych w pracy project managera.

# Teoria o zarabianiu

W ramach realizacji projektów IT funkcjonują dwie główne formy umów.

Pierwszą z nich są tzw. umowy fixed price, które można zdefiniować jako “oczekuję od Ciebie dostarczenia systemu rozwiązującego problemy A, B, C w cenie X na dzień Z”. Podczas wykonywania tego typu projektów konkretny wynik powinien zostać dostarczony w ramach ustalonego budżetu. Sprawa oczywiście nie jest aż tak bardzo zafiksowana, ze względu na istnienie pojęcia [macierzy kompromisów projektowych bazującej na zasadach trójkąta ograniczeń](http://4pm.pl/artykuly/trojkat-ograniczen), które definiuje negocjowalne obszary danego porozumienia. Dla uproszczenia przyjmijmy jednak zasadę “stały budżet, wiadomy efekt”.

Drugą formą umowy dogadania się firmy z klientem jest Time & Materials, która (ponownie w uproszczeniu) zobowiązuje Klienta do ponoszenia kosztu pracy Wykonawcy według ustalonej stawki godzinowej. Przykładowo, wyznaczamy [road mapę](https://en.wikipedia.org/wiki/Technology_roadmap) tworzonego produktu z zaznaczeniem kamieni milowych i na zasadach partnerstwa realizujemy prace wspólnie z Klientem. Taka forma współpracy idealnie sprawdza się w momencie kooperacji ze Startupami, które nie są w stanie zdefiniować pomysłu na wydanie miliona złotych na konkretny cel ze względu na wysoką częstotliwość zmian wymagań biznesowych, szlifowanie modelu biznesowego lub szansę [pivotowania](https://en.wikipedia.org/wiki/Lean_startup#Pivot). Bardzo pomocna do zrozumienia sensu tego typu rozliczania może być lektura książki [Metoda Lean Startup](http://helion.pl/ksiazki/metoda-lean-startup-wykorzystaj-innowacyjne-narzedzia-i-stworz-firme-ktora-zdobedzie-rynek-eric-ries,melean.htm), jako alternatywa do założenia “w projektach IT nie da się nic przewidzieć”.

Z punktu widzenia firmy realizującej dane zlecenie nieodłączną częścią pracy jest raportowanie czasu pracy członków zespołu. Ma to na celu:

*   Mierzenie kosztów realizacji.
*   Obliczanie rentowności naszych działań.
*   Dbanie o budżet klienta.
*   Umożliwienie wczesnego reagowania na ryzyka projektowe.
*   Generowanie zobowiązania programistów/testerów/grafików/designerów/miękkich przez kontrolę estymowanego czasu realizacji vs czasu realnego.
*   W przypadku rozliczeń T&M: fakturowania klienta za przepracowane godziny.

# Problem pierwszy

Trafiając do firmy, należy najczęściej dostosować się do przyzwyczajeń oraz narzędzi w niej wykorzystywanych. Problemem wymienionym na początku tego artykułu jest wykorzystywanie więcej, niż jednego narzędzia w celu realizowania celu, który mógłby zostać zrealizowany przez jedno narzędzie. Idealnym przykładem może być wykorzystywanie issue trackera ([Jira](https://www.atlassian.com/software/jira)) oraz osobnego narzędzia do raportowania przepracowanego przez specjalistów czasu ([Toggl](http://toggl.com/)). W ramach tego artykułu skupimy się na uspójnieniu formy raportowania spalonego czasu z realizowanymi zadaniami zdefiniowanymi w osobnym narzędziu.

# User story

Jako project manager chcę uspójnić dane w obydwu systemach, aby w kolejnych krokach możliwe było ich łatwe połączenie. Pierwszym krokiem do realizacji tego celu będzie stworzenie mechanizmu przepisującego wszystkie utworzone w systemie Jira zadania do systemu Toggl. Ma to na celu, umożliwienie wybrania specjalistom konkretnego zadania z listy rozwijalnej podczas uzupełniania raportu. Dzięki temu unikniemy generycznych raportów znanych również z gitowych commitów: “poprawki”, “fixes” i później będziemy mogli zautomatyzować przenoszenie tych raportów do systemu Jira, który udostępnia świetne funkcjonalności do przechowywania danych oraz generowania raportów. Kroki do rozwiązania tego problemu to:

*   Pobranie zadań konkretnego projektu z systemu Jira przez API.
*   Dodanie zadania do systemu Toggl lub aktualizacja istniejącego zadania w przypadku zmiany Nazwy zadania w Jira z zachowaniem identyfikatora.

# Pierwsze linijki kodu

Wybierając język programowania na potrzeby konkursu Daj się poznać zdecydowałem się na prostotę Pythona (niestety nie było możliwe wyklikanie tego w [Zapierze](https://zapier.com/), w ramach darmowej licencji :)) , która została udowodniona w primaaprilisowym filmie [Gynveala Coldwinda: Gynvael’s Python 101: Hello World!](https://www.youtube.com/watch?v=7VJaprmuHcw). Początkowo przyjmie to formę prostego skryptu, a następnie przeistoczy się w bardziej sensowny soft bazujący na frameworku Django. Mimo prostoty języka, naukę zacząłem od prostego Hello Daj się poznać.

```python
    print("Hello Daj się poznać.")
``` 

Jako project manager uznałem, że najprościej będzie wykorzystać gotowe kawałki kodu do obsłużenia API Jira oraz Toggl. W celu połączenia z Jirą wykorzystam bibliotekę [jira-python](https://jira.readthedocs.io/en/master/), a do obsługi API Toggl użyję [TogglPy autorstwa matthewdowney](https://github.com/matthewdowney/TogglPy). Pierwsza biblioteka została zainstalowana przy użyciu [menadżera pakietów Pip](https://en.wikipedia.org/wiki/Pip_(package_manager)). Druga przez fork, czyli skopiowanie zawartości pliku [TogglPy.py](https://github.com/matthewdowney/TogglPy/blob/master/TogglPy.py) do swojego projektu. Czas na wykorzystanie systemu zarządzania zależnościami jeszcze nadejdzie. :)

Realizacja, w formie dość proceduralnego kodu:

```python
    def get_issues_from_jira(maxResults):
        jira_password = getpass.getpass()
        jira_client = JIRA(config.jira['domain'], basic_auth=(config.jira['username'], jira_password))
    
        jira_issues_json = jira_client.search_issues("project='{0}' ORDER BY created DESC".format(config.jira['project_key']), maxResults=maxResults)
        jira_issues = {}
    
        for issue in jira_issues_json:
            jira_issues[issue.key] = issue.fields.summary
    
        return jira_issues
```   

```python
    def add_issues_to_toggl(jira_issues):
        toggl = TogglPy.Toggl()
        toggl.setAPIKey(config.toggl['token'])
        toggl_issues_json = toggl.request('https://www.toggl.com/api/v8/projects/{0}/tasks'.format(config.toggl['project_id']))
    
        i = 0
        created_count = 0
        updated_count = 0
        toggl_issues = {}
    
        for issue in toggl_issues_json:
            key_last_idx = issue['name'].find(" ")
            issue_key = issue['name'][:key_last_idx]
            issue_summary = issue['name'][key_last_idx+1:]
            toggl_issues[issue_key] = [issue['id'], issue_summary]
    
        jira_issues_count = len(jira_issues.items())
    
        for jira_key, jira_summary in jira_issues.items():
            i += 1
            data = {
                'task': {}
            }
    
            data['task']['name'] = jira_key + " " + jira_summary
            data['task']['pid'] = config.toggl['project_id']
            data['task']['wid'] = config.toggl['workspace_id']
    
            if jira_key in toggl_issues:
                if jira_summary != toggl_issues[jira_key]:        
                    updated_count += 1
                    print "Updating [{0}/{1}] {2} {3}.".decode('ascii', 'ignore').format(str(i), str(jira_issues_count), jira_key, jira_summary)
                    toggl.putRequest('https://www.toggl.com/api/v8/tasks/{0}'.format(toggl_issues[jira_key][0]), data)
            else:
                created_count += 1
                print "Creating [{0}/{1}] {2} {3}.".decode('ascii', 'ignore').format(str(i), str(jira_issues_count), jira_key, jira_summary)
                toggl.postRequest('https://www.toggl.com/api/v8/tasks', data)
    
        print "Number of created Toggl tasks: " + str(created_count)
        print "Number of updated Toggl tasks: " + str(updated_count)
```    

Ustawienia konfiguracyjne są ładowane z pliku `config.py`. Została dodana możliwość uruchamiania skryptu z argumentem `--maxResults` w celu uniknięcia pobierania kompletu zadań przy każdym wykonaniu kodu.

Ciekawostka, na którą się natknąłem to problem z przeprocesowaniem stringu, w którym występują pewne znaki ascii, pojawiający się w momencie wykorzystania interpolacji, który nie występował podczas łączenia stringów plusikiem. Kłopot został ominięty dzięki metodzie `decode('ascii', 'ignore')`.

# Wnioski i cele

*   W bieżącym tygodniu zapoznam się ze [style guidem Pythona](https://www.python.org/dev/peps/pep-0008/) w celu dostosowania się do standardów.
*   Wymienię [Sublime](https://www.sublimetext.com/) na rzecz [PyCharm](https://www.jetbrains.com/pycharm/).
*   Szybciej, niż planowałem zacznę wykorzystywać Django.
*   Poczytam o wykorzystywaniu menadżera zależności w Pythonie.

> Czasem odłożenie pracy na później nie przynosi szkody. Lecz w wypadku baobabu jest to zawsze katastrofa.
> 
> – Antoine de Saint-Exupéry, Katya Longhi. Mały Książe.

* * *

#### Źródła i pojęcia

*   \[1\] [Jak rozmawiać z obcymi formami inteligencji - poradnik dla craftsmanów, Slawomir Sobotka](https://www.youtube.com/watch?v=0XITfxBCYpc&t=7s)
*   \[2\] [Macierz kompromisów projektowych](http://4pm.pl/artykuly/trojkat-ograniczen)
*   \[3\] [Roadmap](https://en.wikipedia.org/wiki/Technology_roadmap)
*   \[4\] [Pivot](https://en.wikipedia.org/wiki/Lean_startup#Pivot)
*   \[5\] [Eric Ries, Metoda Lean Startup](http://helion.pl/ksiazki/metoda-lean-startup-wykorzystaj-innowacyjne-narzedzia-i-stworz-firme-ktora-zdobedzie-rynek-eric-ries,melean.htm)
*   \[6\] [https://www.atlassian.com/software/jira](https://www.atlassian.com/software/jira)
*   \[7\] [http://toggl.com/](http://toggl.com/)
*   \[8\] [https://zapier.com/](https://zapier.com/)
*   \[9\] [Gynveal Coldwind: Gynvael’s Python 101: Hello World!](https://www.youtube.com/watch?v=7VJaprmuHcw)
*   \[10\] [jira-python](https://jira.readthedocs.io/en/master/)
*   \[11\] [TogglPy, matthewdowney](https://github.com/matthewdowney/TogglPy)
*   \[12\] [Pip, Wikipedia](https://en.wikipedia.org/wiki/Pip_(package_manager))
*   \[13\] [Python Style Guide](https://www.python.org/dev/peps/pep-0008/)
*   \[14\] [https://www.sublimetext.com/](https://www.sublimetext.com/)
*   \[15\] [https://www.jetbrains.com/pycharm/](https://www.jetbrains.com/pycharm/)
*   \[16\] Antoine de Saint-Exupéry, Katya Longhi. Mały Książe.
