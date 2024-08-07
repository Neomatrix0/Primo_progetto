
 # PROGETTAZIONE APPLICAZIONE GESTIONE  RISORSE UMANE

## GESTIONE PERSONALE   

Questa applicazione console permetterà la gestione del personale in un azienda,valutando performance,stipendi,mansioni,ore di lavoro e tasso di assenteismo.
Verranno divisi i dipendenti in 2 gruppi in base al punteggio di produttività e verranno segnalati il 15 % dei dipendenti meno performanti.
Mostra i dati relativi a stipendi e  assenze del personale calcolando in percentuale il tasso di assenteismo di ognuno,inoltre
calcola l'incidenza percentuale dello stipendio lordo annuo di ogni dipendente in rapporto al fatturato.


## DEFINIZIONE DEI REQUISITI E ANALISI

L'applicazione consente ad una azienda di monitorare il personale,valutarne le performance e i costi

- [ ] L'applicazione consente di inserire il nome e cognome della persona assunta,età,mansione,score di produttività da 0 a 100,stipendio,tasso di assenteismo,mail aziendale

- [ ] Visualizzazione dei dipendenti inseriti con i relativi dati anagrafici 

- [ ] Possibilità di visionare gli stipendi annuali di ogni dipendente

- [ ] Valutazione performance dei dipendenti e indicazione del 15% dei dipendenti meno performanti

- [ ] Incidenza percentuale dello stipendio lordo del dipendente sul fatturato su base annuale


## PIANIFICAZIONE E DESIGN DELL'ARCHITETTURA

- [ ] Impostazione del menu generale con opzioni di scelta

- [ ] Opzione di inserimento del personale con dati inseriti in modo intervallato da virgola(Split),dettagli anagrafici,stipendio,mansione,contratto,performance,assenze e salvataggio dati nel file json

- [ ] Opzione di visualizzazione di tutto il personale con i relativi dati

- [ ]  Opzione di ricerca del singolo dipendente inserendo nome,cognome

- [ ]  Modifica dati dipendente e implementazione di un sottomenu per scegliere il singolo campo da modificare

- [ ] In caso di cambiamento di nome e cognome tale modifica deve riflettersi non solo all'interno del json,ma anche cambiandone il nome

- [ ] Rimozione dipendente dal programma con relativo file json

- [ ] Valutazione performance i dipendenti vengono divisi in 2 gruppi in base al livello della performance e viene segnalato il 15% dei dipendenti con le performance più basse il in questo sottomenu

- [ ] Calcolo assenteismo scrivendo nome e cognome  del dipendente l'utente inserisce  le ore lavorate e viene calcolato il tasso di assenteismo(assenze/ giorni da lavorare)*100

- [ ] Ordina stipendio dal più alto al più basso mostrando a schermo mansione e dati anagrafici

- [ ] Calcolo incidenza percentuale dello stipendio lordo sul fatturato.Il fatturato viene registrato su un file txt che poi dovrà essere aggiornato dall'utente manualmente 

## AGGIUNTE EXTRA

- [ ]  Integrazione di Spectre console per rendere il menu user friendly e per ordinare i dati in tabelle

- [ ] creazione di un sotto menu all'interno della funzione ModificaDipendente per scegliere il singolo campo da modificare

- [ ]  Modificare alcune funzioni inserendo parametri
   
- [ ]  Integrare try and catch per gestione delle eccezioni

- [ ]  Aggiungere un campo per identificare il dipendente ovvero la mail aziendale

- [ ]  Aggiungere funzione per calcolare incidenza percentuale dello stipendio lordo sul fatturato.Il fatturato viene scritto su file



## DEFINIZIONE DI STRUTTURE E CONVENZIONI

Di seguito le  convenzioni di codifica e i nomi standard utilizzati.

 - [ ]  I nomi delle classi devono essere PascalCase.
 - [ ]  I nomi dei metodi devono essere PascalCase.
 - [ ]  I nomi delle variabili devono essere camelCase.
 - [ ]  I nomi delle costanti devono essere UPPERCASE.
 - [ ]  I nomi dei file devono essere lowercase.
 - [ ]  I nomi dei progetti devono essere PascalCase.
 - [ ]  I nomi dei namespace devono essere PascalCase.

 ## STRUTTURA JSON

 - Di seguito il modello di formattazione del file json di ogni dipendente inclusivo di tutti i dati

 ```json

 {
  "Nome": "fabio",
  "Cognome": "fabrizi",
  "DataDiNascita": "10/02/1976",
  "Mansione": "impiegato",
  "Stipendio": 23000.0,
  "Performance": 30,
  "Assenze": 40,
  "Mail": "fabio.fabrizi@gmail.com"
}

 ```


## SVILUPPO DEI COMPONENTI
Ora che abbiamo definito le convenzioni di codifica e i nomi standard, possiamo iniziare a scrivere il codice. In questo caso, creeremo un progetto console per l'applicazione e un progetto di test per i test unitari.

- [ ] Creare un progetto console per l'applicazione.
- [ ] Creare un progetto di test per i test unitari.

## TEST E DEBUGGING
Ora che abbiamo integrato i componenti dell'applicazione, dobbiamo testarli e risolvere eventuali bug. In questo caso, scriveremo test unitari per i componenti dell'applicazione.

 - [ ] Scrivere test unitari per i componenti dell'applicazione.
 - [ ] Eseguire il debugging per individuare e risolvere i bug



## DOCUMENTAZIONE

Ora che abbiamo testato e risolto i bug dell'applicazione, dobbiamo documentare il codice e l'architettura. In questo caso, documenteremo il codice e l'architettura dell'applicazione.

 - [ ] Documentare il codice e l'architettura dell'applicazione.

 - [ ] Documentare i test unitari.

 - [ ] Documentare la fase di Beta Testing.

 - [ ] Documentare la fase di post Beta Testing.


## SCHEDULE 
```mermaid

gantt
    title A Gantt Diagram
    dateFormat YYYY-MM-DD
    section Section
        Giorno 1 impostazione menu    :a1, 2024-07-22, 1d
        Giorno 2 lavoro su funzioni   :a2, 2024-07-23, 1d
        Giorno 3 Persistenza dei dati :a3, 2024-07-24, 1d
        Giorno 4 funzionalità + spectre :a4, 2024-07-25, 1d
        Giorno 5 Fine applicazione    :a5, 2024-07-26, 1d
        Giorno 6 Refactoring codice   :a6, 2024-07-27, 1d





   
```


## FLOWCHART APPLICAZIONE
```mermaid



   flowchart TD
    A[Start] --> B{Menu Principale}
    B -- 1 --> C[/Inserisci dipendente con i dati/] --> Z
    B -- 2 --> D[visualizza dipendenti] --> Z
    B -- 3 --> E[cerca dipendente] --> Z
    B -- 4 --> F[modifica dipendente] --> F1{sottomenu scelta campo da modificare} --> F2[cambia proprietà dipendente]--> Z
    B -- 5 --> G[rimuovi dipendente] --> Z
    B -- 6 --> H[calcola tasso di assenteismo ] --> Z
    B -- 7 --> I[performance indicatore] --> O[topPerformance] & O1[lowPerformance] --> Z
    B -- 8 --> L[ordina stipendio] --> Z
    B -- 9 --> L[Incidenza stipendio/fatturato] --> Z
    B -- 10 --> N[esci dall'applicazione] --> Z
    Z[end] --loop --> B

```

# COMANDI VERSIONAMENTO

```bash

git status
git add --all
git commit -m "first-commit"
git push -u origin main

```


#  PRIMA VERSIONE DEL CODICE SEMPLIFICATA

- Creazione del menu principale con possibilità di uscita dal gioco
- Creazione oggetto  dipendenti per contenere i dati che serviranno per le varie funzionalità
- Creazione della cartella dipendenti dove verranno aggiunti i file json di ogni dipendente
- Implementate funzioni InserisciDipendente,VisualizzaDipendente,CercaDipendente contestualmente introdotta persistenza dei dati
    - InserisciDipendente permette di inserire da console tutti i dati del dipendente,divisi dalla virgola per poi registrarli nel json. 
    - Verrà generato un file json diverso per ogni singolo dipendente.Ogni file verrà rinominato con il nome e cognome del dipedenene
    - VisualizzaDipendente permette di vedere tutti i dati dei dipendenti
    - CercaDipendente permette di cercare un singolo dipendente e vederne i dati scrivendo sulla console nome,cognome
- Implementata funzione StampaDati per evitare ridondanze nel codice e stampare le proprietà dei dipendenti


<details>

<summary>Visualizza il codice</summary>

```c#

using Newtonsoft.Json;


class Program
{

    // crea cartella dipendenti dove verranno messi i file json per ogni dipendente
    static string directoryPath = @"dipendenti/";

    static void Main(string[] args)

    {
        // se la cartella non esiste la crea

        if (!Directory.Exists(directoryPath))
        {
            Directory.CreateDirectory(directoryPath);
        }

        Console.WriteLine("Benvenuto nel programma di gestione del personale.");
        int opzione;

        do
        {
            Console.Clear();
            Console.WriteLine("1. Inserisci dipendente");
            Console.WriteLine("2. Visualizza dipendenti");
            Console.WriteLine("3. Cerca dipendente");
            Console.WriteLine("4. Esci\n");

            // scelta del tipo di azione da svolgere

            opzione = Convert.ToInt32(Console.ReadLine());
            switch (opzione)
            {
                case 1:
                    InserisciDipendente();
                    break;
                case 2:
                    VisualizzaDipendenti();
                    break;
                case 3:
                    CercaDipendente();
                    break;
           
                case 4:
                    Console.WriteLine("Il programma verrà chiuso. Attendere prego.");
                    break;
                default:
                    Console.WriteLine("Errore di scelta: Prego riprovare");
                    break;
            }

            // se viene scelta l'opzione 9 il programma si chiude altrimenti prosegue

            if (opzione != 4)
            {
                Console.WriteLine("\nPremere un tasto per proseguire");
                Console.ReadKey();
            }

        } while (opzione != 4);
    }

    static void InserisciDipendente()
    {
        do
        {
            try
            {
                Console.WriteLine("Inserisci nome, cognome, data di nascita DD/MM/YYYY,mansione, stipendio,voto performance da 1 a 100 ,giorni di assenze,separate da virgola");

                // accetta l'input dei dati da console
                string? inserimento = Console.ReadLine();

                // permette l'inserimento di più valori divisi dalla virgola

                string[] dati = inserimento.Split(',');

                // formattazione data di nascita
                //ParseExact permette di specificare esattamente come vogliamo il formato  della data converte da stringa a oggetto Datetime

                DateTime dataDiNascita = DateTime.ParseExact(dati[2].Trim(), "dd/MM/yyyy", null);

                //viene riconvertito in stringa
                string dataDiNascitaFormatted = dataDiNascita.ToString("dd/MM/yyyy");

                //  creazione di un oggetto dipendente contenente i dati richiesti dall'applicazione
                var dipendente = new
                {
                    Nome = dati[0].Trim(),
                    Cognome = dati[1].Trim(),
                    DataDiNascita = dataDiNascitaFormatted, //DateTime.Parse(dati[2].Trim()),
                    Mansione = dati[3].Trim(),
                    Stipendio = Convert.ToDecimal(dati[4].Trim()),
                    Performance = Convert.ToInt32(dati[5].Trim()),
                    Assenze = Convert.ToInt32(dati[6].Trim()),
                    Mail = dati[7].Trim()
                };

                // serializza l'oggetto in una stringa Json e lo indenta per renderlo più leggibile

                string jsonString = JsonConvert.SerializeObject(dipendente, Formatting.Indented);

                // Path.Combine concatena il path della cartella dipendenti al path dei file json di ogni dipendente
                string filePath = Path.Combine(directoryPath, $"{dipendente.Nome}_{dipendente.Cognome}.json");

                //scrive il file

                File.WriteAllText(filePath, jsonString);

            }
            catch (Exception e)
            {
                Console.WriteLine($"ERRORE INSERIMENTO DATI: {e.Message}");     // messaggio eccezione
                Console.WriteLine($"CODICE ERRORE:{e.HResult}");                //codice numerico eccezione
                return;
            }

            // se si svuole terminare l'immissione della registrazione del dipendente basta digitare n

            Console.WriteLine("Vuoi inserire un altro dipendente? (s/n)");
            string? risposta = Console.ReadLine().Trim().ToLower();
            if (risposta == "n")
            {
                break;
            }
        } while (true);
    }

    // creazione dei metodi per ogni singola funzionalità
    static void VisualizzaDipendenti()
    {
        // analizza tutti i file con estensione .json dentro la directoryPath(cartella dipendenti)
        var files = Directory.GetFiles(directoryPath, "*.json");  //

        // verifica se c'è almeno un file per eseguire il codice
        if (files.Length > 0)
        {
            Console.WriteLine("Lista dipendenti completa con tutti i dati:\n");

            // stampa i dati di tutti i dipendenti presi dai json

            foreach (var file in files)
            {

                StampaDati(file);

            }
        }
        else
        {
            Console.WriteLine("Nessun dipendente nel database.");
        }
    }

    // metodo per cercare il dipendente
    static void CercaDipendente()
    {
        try
        {
            Console.WriteLine("\nInserisci nome e cognome del dipendente che vuoi cercare separati da virgola");
            var inserisciNome = Console.ReadLine();

            // permette l'inserimento di molteplici input separati dalla virgola quindi permette un array di stringhe con nome cognome
            var nomi = inserisciNome.Split(',');

            // il dipendente deve essere cercato inserendo nome,cognome se vengono inseriti più valori viene gestito l'errore


            if (nomi.Length != 2)
            {
                throw new FormatException("L'input deve contenere esattamente due valori separati da virgola: nome e cognome.");
                //Console.WriteLine("Nomi non validi");
                //return;
            }

            // creato variabili per associarvi il valore di nome e cognome relativi all'array nomi

            string nome = nomi[0].Trim();
            string cognome = nomi[1].Trim();

            // nome e cognome di ogni dipendente diventerenno il rispettivo nome dei file json 
            string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

            // verifica se un file json esiste

            if (File.Exists(filePath))
            {

                StampaDati(filePath);
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore non trattato: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }
      static void StampaDati(string filePath)
    {
        // legge il contenuto del file json
        string jsonRead = File.ReadAllText(filePath);
        // deserializza la stringa JSON in un oggetto di tipo dynamic
        var dipendente = JsonConvert.DeserializeObject<dynamic>(jsonRead);
        Console.WriteLine($"\nNome: {dipendente.Nome}");
        Console.WriteLine($"Cognome: {dipendente.Cognome}");
        Console.WriteLine($"Data di nascita: {dipendente.DataDiNascita}");
        Console.WriteLine($"Mansione: {dipendente.Mansione}");
        Console.WriteLine($"Stipendio: {dipendente.Stipendio}");
        Console.WriteLine($"Performance: {dipendente.Performance}");
        Console.WriteLine($"Giorni di assenza: {dipendente.Assenze}");
        Console.WriteLine($"Mail: {dipendente.Mail}");

    }

}
```

</details>



# IMPLEMENTAZIONI VERSIONE 2

- Modifica del menu principale aggiungendo nuovi case per accogliere le nuove funzioni
- Aggiunta funzione ModificaDipendente(),creando un sottomenu dove scegliere il singolo campo da modificare.La modifica si rifletterà anche nel rispettivo json
- Aggiunta della funzione RimuoviDipendente() per rimuovere il singolo dipendente dal programma e il relativo file json inserendo nome,cognome

<details>
    <summary>Visualizza il codice</summary>

 ```c#

using Newtonsoft.Json;


class Program
{

    // crea cartella dipendenti dove verranno messi i file json per ogni dipendente
    static string directoryPath = @"dipendenti/";

    static void Main(string[] args)

    {
        // se la cartella non esiste la crea

        if (!Directory.Exists(directoryPath))
        {
            Directory.CreateDirectory(directoryPath);
        }

        Console.WriteLine("Benvenuto nel programma di gestione del personale.");
        int opzione;

        do
        {
            Console.Clear();
            Console.WriteLine("1. Inserisci dipendente");
            Console.WriteLine("2. Visualizza dipendenti");
            Console.WriteLine("3. Cerca dipendente");
            Console.WriteLine("4. Modifica dipendente");
            Console.WriteLine("5. Rimuovi dipendente");
           //  Console.WriteLine("6. Tasso di assenteismo");
           // Console.WriteLine("7. Indicatore di performance");
          //  Console.WriteLine("8. Ordina per stipendio");
            Console.WriteLine("9. Esci\n");

            // scelta del tipo di azione da svolgere

            opzione = Convert.ToInt32(Console.ReadLine());
            switch (opzione)
            {
                case 1:
                    InserisciDipendente();
                    break;
                case 2:
                    VisualizzaDipendenti();
                    break;
                case 3:
                    CercaDipendente();
                    break;
                case 4:
                    ModificaDipendente();
                    break;
                case 5:
                    RimuoviDipendente();
                    break;
                case 6:
                  //  TassoDiAssenteismo();
                    break;
                case 7:

                   // ValutazionePerformance();
                    break;
                case 8:

                  //  SortStipendio();
                    break;
                case 9:
                    Console.WriteLine("Il programma verrà chiuso. Attendere prego.");
                    break;
                default:
                    Console.WriteLine("Errore di scelta: Prego riprovare");
                    break;
            }

            // se viene scelta l'opzione 9 il programma si chiude altrimenti prosegue

            if (opzione != 9)
            {
                Console.WriteLine("\nPremere un tasto per proseguire");
                Console.ReadKey();
            }

        } while (opzione != 9);
    }

    static void InserisciDipendente()
    {
        do
        {
            try
            {
                Console.WriteLine("Inserisci nome, cognome, data di nascita DD/MM/YYYY,mansione, stipendio,voto performance da 1 a 100 ,giorni di assenze,mail,separate da virgola");

                // accetta l'input dei dati da console
                string? inserimento = Console.ReadLine();

                // permette l'inserimento di più valori divisi dalla virgola

                string?[] dati = inserimento.Split(',')!;

                // formattazione data di nascita
                //ParseExact permette di specificare esattamente come vogliamo il formato  della data converte da stringa a oggetto Datetime

                DateTime dataDiNascita = DateTime.ParseExact(dati[2].Trim(), "dd/MM/yyyy", null);

                //viene riconvertito in stringa
                string dataDiNascitaFormatted = dataDiNascita.ToString("dd/MM/yyyy");

                //  creazione di un oggetto dipendente contenente i dati richiesti dall'applicazione
                var dipendente = new
                {
                    Nome = dati[0].Trim(),
                    Cognome = dati[1].Trim(),
                    DataDiNascita = dataDiNascitaFormatted, //DateTime.Parse(dati[2].Trim()),
                    Mansione = dati[3].Trim(),
                    Stipendio = Convert.ToDecimal(dati[4].Trim()),
                    Performance = Convert.ToInt32(dati[5].Trim()),
                    Assenze = Convert.ToInt32(dati[6].Trim()),
                    Mail = dati[7].Trim()
                };

                // serializza l'oggetto in una stringa Json e lo indenta per renderlo più leggibile

                string jsonString = JsonConvert.SerializeObject(dipendente, Formatting.Indented);

                // Path.Combine concatena il path della cartella dipendenti al path dei file json di ogni dipendente
                string filePath = Path.Combine(directoryPath, $"{dipendente.Nome}_{dipendente.Cognome}.json");

                //scrive il file

                File.WriteAllText(filePath, jsonString);

            }
            catch (Exception e)
            {
                Console.WriteLine($"ERRORE INSERIMENTO DATI: {e.Message}");     // messaggio eccezione
                Console.WriteLine($"CODICE ERRORE:{e.HResult}");                //codice numerico eccezione
                return;
            }

            // se si svuole terminare l'immissione della registrazione del dipendente basta digitare n

            Console.WriteLine("Vuoi inserire un altro dipendente? (s/n)");
            string? risposta = Console.ReadLine().Trim().ToLower();
            if (risposta == "n")
            {
                break;
            }
        } while (true);
    }

    // creazione dei metodi per ogni singola funzionalità
    static void VisualizzaDipendenti()
    {
        // analizza tutti i file con estensione .json dentro la directoryPath(cartella dipendenti)
        var files = Directory.GetFiles(directoryPath, "*.json");  //

        // verifica se c'è almeno un file per eseguire il codice
        if (files.Length > 0)
        {
            Console.WriteLine("Lista dipendenti completa con tutti i dati:\n");

            // stampa i dati di tutti i dipendenti presi dai json

            foreach (var file in files)
            {

                StampaDati(file);

            }
        }
        else
        {
            Console.WriteLine("Nessun dipendente nel database.");
        }
    }

    // metodo per cercare il dipendente
    static void CercaDipendente()
    {
        try
        {
            Console.WriteLine("\nInserisci nome e cognome del dipendente che vuoi cercare separati da virgola");
            var inserisciNome = Console.ReadLine();

            // permette l'inserimento di molteplici input separati dalla virgola quindi permette un array di stringhe con nome cognome
            var nomi = inserisciNome.Split(',');

            // il dipendente deve essere cercato inserendo nome,cognome se vengono inseriti più valori viene gestito l'errore


            if (nomi.Length != 2)
            {
                throw new FormatException("L'input deve contenere esattamente due valori separati da virgola: nome e cognome.");
              
            }

            // creato variabili per associarvi il valore di nome e cognome relativi all'array nomi

            string nome = nomi[0].Trim();
            string cognome = nomi[1].Trim();

            // nome e cognome di ogni dipendente diventerenno il rispettivo nome dei file json 
            string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

            // verifica se un file json esiste

            if (File.Exists(filePath))
            {

                StampaDati(filePath);
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore non trattato: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }
    //cerca dipendente per nome e cognome e poi modifica le caratteristiche del dipendente a scelta

    static void ModificaDipendente()
    {
        Console.WriteLine("\nInserisci nome e cognome del dipendente che vuoi modificare separati da virgola");
        var inserisciNome = Console.ReadLine();
        var nomi = inserisciNome.Split(',');

        // il dipendente va cercato solo inserendo nome,cognome

        if (nomi.Length != 2)
        {
            Console.WriteLine("Nomi non validi");
            return;
        }

        // Trim() rimuove gli spazi vuoti dal nome e cognome

        string nome = nomi[0].Trim();
        string cognome = nomi[1].Trim();
        string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

        if (File.Exists(filePath))
        {
            string jsonRead = File.ReadAllText(filePath);
            var lavoratore = JsonConvert.DeserializeObject<dynamic>(jsonRead);

            // sottomenu per scegliere il valore da modificare

            Console.WriteLine("1. Cambia nome");
            Console.WriteLine("2. Cambia cognome");
            Console.WriteLine("3. Cambia data di nascita sempre nel formato DD/MM/YY");
            Console.WriteLine("4. Cambia mansione");
            Console.WriteLine("5. Cambia stipendio");
            Console.WriteLine("6. Cambia punteggio performance");
            Console.WriteLine("7. Cambia giorni di assenze");
            Console.WriteLine("8. Cambia mail");
            Console.WriteLine("9. Esci");

            // scelta del valore da cambiare

            int inserimento = Convert.ToInt32(Console.ReadLine());



            switch (inserimento)
            {


                case 1:

                    Console.WriteLine("Inserici il nuovo nome");
                    lavoratore.Nome = Console.ReadLine().Trim();



                    break;

                case 2:
                    Console.WriteLine("Inserici il nuovo cognome");
                    lavoratore.Cognome = Console.ReadLine().Trim();


                    break;

                case 3:
                    Console.WriteLine("Inserisci nuova data di nascita");
                    lavoratore.DataDiNascita = DateTime.ParseExact(Console.ReadLine().Trim(), "dd/MM/yyyy", null).ToString("dd/MM/yyyy");

                    break;

                case 4:
                    Console.WriteLine("Inserisci nuova mansione");
                    lavoratore.Mansione = Console.ReadLine().Trim();


                    break;

                case 5:
                    Console.WriteLine("Inserisci nuovo stipendio");
                    lavoratore.Stipendio = Convert.ToDecimal(Console.ReadLine());

                    break;

                case 6:
                    Console.WriteLine("Inserisci nuovo punteggio performance");
                    lavoratore.Performance = Convert.ToInt32(Console.ReadLine());

                    break;

                case 7:
                    Console.WriteLine("Modifica giorni di assenze");
                    lavoratore.Assenze = Convert.ToInt32(Console.ReadLine());

                    break;

                 case 8:
                    Console.WriteLine("Modifica giorni di assenze");
                    lavoratore.Mail = Console.ReadLine();

                    break;

                case 9:
                    Console.WriteLine("\nL'applicazione si sta per chiudere\n");

                    break;

                default:
                    Console.WriteLine("\nScelta errata.Prego scegliere tra le opzioni disponibili 1-8\n");
                    break;
            }

            // se nome,cognome vengono modificati cambia anche il nome del json corrispondente

            string newFilePath = Path.Combine(directoryPath, $"{lavoratore.Nome}_{lavoratore.Cognome}.json");

            // Serializza i dati aggiornati del dipendente 
            string jsonString = JsonConvert.SerializeObject(lavoratore, Formatting.Indented);

            //Cancella il vecchio json

            File.Delete(filePath);

            //scrive il nuovo file json con i dati aggiornati serializzati

            File.WriteAllText(newFilePath, jsonString);


            Console.WriteLine("Dipendente aggiornato con successo.");
        }
        else
        {
            Console.WriteLine("Dipendente non trovato");
        }
    }

      static void StampaDati(string filePath)
    {
        // legge il contenuto del file json
        string jsonRead = File.ReadAllText(filePath);
        // deserializza la stringa JSON in un oggetto di tipo dynamic
        var dipendente = JsonConvert.DeserializeObject<dynamic>(jsonRead);
        Console.WriteLine($"\nNome: {dipendente.Nome}");
        Console.WriteLine($"Cognome: {dipendente.Cognome}");
        Console.WriteLine($"Data di nascita: {dipendente.DataDiNascita}");
        Console.WriteLine($"Mansione: {dipendente.Mansione}");
        Console.WriteLine($"Stipendio: {dipendente.Stipendio}");
        Console.WriteLine($"Performance: {dipendente.Performance}");
        Console.WriteLine($"Giorni di assenza: {dipendente.Assenze}");
        Console.WriteLine($"Giorni di assenza: {dipendente.Mail}");

    }

    static void RimuoviDipendente()
    {
        Console.WriteLine("Inserisci nome e cognome del dipendente che vuoi rimuovere separati da virgola");
        var inserisciNome = Console.ReadLine();
        var nomi = inserisciNome.Split(',');

        if (nomi.Length != 2)
        {
            Console.WriteLine("Nomi non validi");
            return;
        }

        string nome = nomi[0].Trim();
        string cognome = nomi[1].Trim();
        string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

        if (File.Exists(filePath))
        {
            File.Delete(filePath);    // rimuove file json
            Console.WriteLine("Dipendente rimosso con successo.");
        }
        else
        {
            Console.WriteLine("Dipendente non trovato");
        }
    }

   

}

```

</details>


# IMPLEMENTAZIONI VERSIONE 3

- Aggiunta funzione TassoDiAssenteismo() calcola rapporto percentuale dei giorni di assenza rispetto ai 250 giorni lavorativi all'anno
- Aggiunta funzione ValutazionePerformance() ordina i dipendenti per performance e li divide in 2 gruppi.
La prima metà sono i dipendenti con i punteggi più alti la seconda squadra includerà i dipendenti con punteggi più bassi.
Vengono segnalati  anche i dipedendenti con il 15% delle performance peggiori
- Aggiunta funzione SortStipendio() ordina i dipendenti dallo stipendio più alto al più basso

<details>
    <summary>Visualizza il codice</summary>

 ```c#

using Newtonsoft.Json;


class Program
{

    // crea cartella dipendenti dove verranno messi i file json per ogni dipendente
    static string directoryPath = @"dipendenti/";

    static void Main(string[] args)

    {
        // se la cartella non esiste la crea

        if (!Directory.Exists(directoryPath))
        {
            Directory.CreateDirectory(directoryPath);
        }

        Console.WriteLine("Benvenuto nel programma di gestione del personale.");
        int opzione;

        do
        {
            Console.Clear();
            Console.WriteLine("1. Inserisci dipendente");
            Console.WriteLine("2. Visualizza dipendenti");
            Console.WriteLine("3. Cerca dipendente");
            Console.WriteLine("4. Modifica dipendente");
            Console.WriteLine("5. Rimuovi dipendente");
            Console.WriteLine("6. Tasso di assenteismo");
            Console.WriteLine("7. Indicatore di performance");
            Console.WriteLine("8. Ordina per stipendio");
            Console.WriteLine("9. Esci\n");

            // scelta del tipo di azione da svolgere

            opzione = Convert.ToInt32(Console.ReadLine());
            switch (opzione)
            {
                case 1:
                    InserisciDipendente();
                    break;
                case 2:
                    VisualizzaDipendenti();
                    break;
                case 3:
                    CercaDipendente();
                    break;
                case 4:
                    ModificaDipendente();
                    break;
                case 5:
                    RimuoviDipendente();
                    break;
                case 6:
                    TassoDiAssenteismo();
                    break;
                case 7:

                    ValutazionePerformance();
                    break;
                case 8:

                    SortStipendio();
                    break;
                case 9:
                    Console.WriteLine("Il programma verrà chiuso. Attendere prego.");
                    break;
                default:
                    Console.WriteLine("Errore di scelta: Prego riprovare");
                    break;
            }

            // se viene scelta l'opzione 9 il programma si chiude altrimenti prosegue

            if (opzione != 9)
            {
                Console.WriteLine("\nPremere un tasto per proseguire");
                Console.ReadKey();
            }

        } while (opzione != 9);
    }

    static void InserisciDipendente()
    {
        do
        {
            try
            {
                Console.WriteLine("Inserisci nome, cognome, data di nascita DD/MM/YYYY,mansione, stipendio,voto performance da 1 a 100 ,giorni di assenze,mail,separate da virgola");

                // accetta l'input dei dati da console
                string? inserimento = Console.ReadLine();

                // permette l'inserimento di più valori divisi dalla virgola

                string?[] dati = inserimento.Split(',')!;

                // formattazione data di nascita
                //ParseExact permette di specificare esattamente come vogliamo il formato  della data converte da stringa a oggetto Datetime

                DateTime dataDiNascita = DateTime.ParseExact(dati[2].Trim(), "dd/MM/yyyy", null);

                //viene riconvertito in stringa
                string dataDiNascitaFormatted = dataDiNascita.ToString("dd/MM/yyyy");

                //  creazione di un oggetto dipendente contenente i dati richiesti dall'applicazione
                var dipendente = new
                {
                    Nome = dati[0].Trim(),
                    Cognome = dati[1].Trim(),
                    DataDiNascita = dataDiNascitaFormatted, //DateTime.Parse(dati[2].Trim()),
                    Mansione = dati[3].Trim(),
                    Stipendio = Convert.ToDecimal(dati[4].Trim()),
                    Performance = Convert.ToInt32(dati[5].Trim()),
                    Assenze = Convert.ToInt32(dati[6].Trim()),
                    Mail = dati[7].Trim()
                };

                // serializza l'oggetto in una stringa Json e lo indenta per renderlo più leggibile

                string jsonString = JsonConvert.SerializeObject(dipendente, Formatting.Indented);

                // Path.Combine concatena il path della cartella dipendenti al path dei file json di ogni dipendente
                string filePath = Path.Combine(directoryPath, $"{dipendente.Nome}_{dipendente.Cognome}.json");

                //scrive il file

                File.WriteAllText(filePath, jsonString);

            }
            catch (Exception e)
            {
                Console.WriteLine($"ERRORE INSERIMENTO DATI: {e.Message}");     // messaggio eccezione
                Console.WriteLine($"CODICE ERRORE:{e.HResult}");                //codice numerico eccezione
                return;
            }

            // se si svuole terminare l'immissione della registrazione del dipendente basta digitare n

            Console.WriteLine("Vuoi inserire un altro dipendente? (s/n)");
            string? risposta = Console.ReadLine().Trim().ToLower();
            if (risposta == "n")
            {
                break;
            }
        } while (true);
    }

    // creazione dei metodi per ogni singola funzionalità
    static void VisualizzaDipendenti()
    {
        // analizza tutti i file con estensione .json dentro la directoryPath(cartella dipendenti)
        var files = Directory.GetFiles(directoryPath, "*.json");  //

        // verifica se c'è almeno un file per eseguire il codice
        if (files.Length > 0)
        {
            Console.WriteLine("Lista dipendenti completa con tutti i dati:\n");

            // stampa i dati di tutti i dipendenti presi dai json

            foreach (var file in files)
            {

                StampaDati(file);

            }
        }
        else
        {
            Console.WriteLine("Nessun dipendente nel database.");
        }
    }

    // metodo per cercare il dipendente
    static void CercaDipendente()
    {
        try
        {
            Console.WriteLine("\nInserisci nome e cognome del dipendente che vuoi cercare separati da virgola");
            var inserisciNome = Console.ReadLine();

            // permette l'inserimento di molteplici input separati dalla virgola quindi permette un array di stringhe con nome cognome
            var nomi = inserisciNome.Split(',');

            // il dipendente deve essere cercato inserendo nome,cognome se vengono inseriti più valori viene gestito l'errore


            if (nomi.Length != 2)
            {
                throw new FormatException("L'input deve contenere esattamente due valori separati da virgola: nome e cognome.");
              
            }

            // creato variabili per associarvi il valore di nome e cognome relativi all'array nomi

            string nome = nomi[0].Trim();
            string cognome = nomi[1].Trim();

            // nome e cognome di ogni dipendente diventerenno il rispettivo nome dei file json 
            string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

            // verifica se un file json esiste

            if (File.Exists(filePath))
            {

                StampaDati(filePath);
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore non trattato: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }
    //cerca dipendente per nome e cognome e poi modifica le caratteristiche del dipendente a scelta

    static void ModificaDipendente()
    {
        Console.WriteLine("\nInserisci nome e cognome del dipendente che vuoi modificare separati da virgola");
        var inserisciNome = Console.ReadLine();
        var nomi = inserisciNome.Split(',');

        // il dipendente va cercato solo inserendo nome,cognome

        if (nomi.Length != 2)
        {
            Console.WriteLine("Nomi non validi");
            return;
        }

        // Trim() rimuove gli spazi vuoti dal nome e cognome

        string nome = nomi[0].Trim();
        string cognome = nomi[1].Trim();
        string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

        if (File.Exists(filePath))
        {
            string jsonRead = File.ReadAllText(filePath);
            var lavoratore = JsonConvert.DeserializeObject<dynamic>(jsonRead);

            // sottomenu per scegliere il valore da modificare

            Console.WriteLine("1. Cambia nome");
            Console.WriteLine("2. Cambia cognome");
            Console.WriteLine("3. Cambia data di nascita sempre nel formato DD/MM/YY");
            Console.WriteLine("4. Cambia mansione");
            Console.WriteLine("5. Cambia stipendio");
            Console.WriteLine("6. Cambia punteggio performance");
            Console.WriteLine("7. Cambia giorni di assenze");
            Console.WriteLine("8. Cambia mail");
            Console.WriteLine("9. Esci");

            // scelta del valore da cambiare

            int inserimento = Convert.ToInt32(Console.ReadLine());



            switch (inserimento)
            {


                case 1:

                    Console.WriteLine("Inserici il nuovo nome");
                    lavoratore.Nome = Console.ReadLine().Trim();



                    break;

                case 2:
                    Console.WriteLine("Inserici il nuovo cognome");
                    lavoratore.Cognome = Console.ReadLine().Trim();


                    break;

                case 3:
                    Console.WriteLine("Inserisci nuova data di nascita");
                    lavoratore.DataDiNascita = DateTime.ParseExact(Console.ReadLine().Trim(), "dd/MM/yyyy", null).ToString("dd/MM/yyyy");

                    break;

                case 4:
                    Console.WriteLine("Inserisci nuova mansione");
                    lavoratore.Mansione = Console.ReadLine().Trim();


                    break;

                case 5:
                    Console.WriteLine("Inserisci nuovo stipendio");
                    lavoratore.Stipendio = Convert.ToDecimal(Console.ReadLine());

                    break;

                case 6:
                    Console.WriteLine("Inserisci nuovo punteggio performance");
                    lavoratore.Performance = Convert.ToInt32(Console.ReadLine());

                    break;

                case 7:
                    Console.WriteLine("Modifica giorni di assenze");
                    lavoratore.Assenze = Convert.ToInt32(Console.ReadLine());

                    break;

                 case 8:
                    Console.WriteLine("Modifica giorni di assenze");
                    lavoratore.Mail = Console.ReadLine();

                    break;

                case 9:
                    Console.WriteLine("\nL'applicazione si sta per chiudere\n");

                    break;

                default:
                    Console.WriteLine("\nScelta errata.Prego scegliere tra le opzioni disponibili 1-8\n");
                    break;
            }

            // se nome,cognome vengono modificati cambia anche il nome del json corrispondente

            string newFilePath = Path.Combine(directoryPath, $"{lavoratore.Nome}_{lavoratore.Cognome}.json");

            // Serializza i dati aggiornati del dipendente 
            string jsonString = JsonConvert.SerializeObject(lavoratore, Formatting.Indented);

            //Cancella il vecchio json

            File.Delete(filePath);

            //scrive il nuovo file json con i dati aggiornati serializzati

            File.WriteAllText(newFilePath, jsonString);


            Console.WriteLine("Dipendente aggiornato con successo.");
        }
        else
        {
            Console.WriteLine("Dipendente non trovato");
        }
    }

      static void StampaDati(string filePath)
    {
        // legge il contenuto del file json
        string jsonRead = File.ReadAllText(filePath);
        // deserializza la stringa JSON in un oggetto di tipo dynamic
        var dipendente = JsonConvert.DeserializeObject<dynamic>(jsonRead);
        Console.WriteLine($"\nNome: {dipendente.Nome}");
        Console.WriteLine($"Cognome: {dipendente.Cognome}");
        Console.WriteLine($"Data di nascita: {dipendente.DataDiNascita}");
        Console.WriteLine($"Mansione: {dipendente.Mansione}");
        Console.WriteLine($"Stipendio: {dipendente.Stipendio}");
        Console.WriteLine($"Performance: {dipendente.Performance}");
        Console.WriteLine($"Giorni di assenza: {dipendente.Assenze}");
        Console.WriteLine($"Giorni di assenza: {dipendente.Mail}");

    }

    static void RimuoviDipendente()
    {
        Console.WriteLine("Inserisci nome e cognome del dipendente che vuoi rimuovere separati da virgola");
        var inserisciNome = Console.ReadLine();
        var nomi = inserisciNome.Split(',');

        if (nomi.Length != 2)
        {
            Console.WriteLine("Nomi non validi");
            return;
        }

        string nome = nomi[0].Trim();
        string cognome = nomi[1].Trim();
        string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

        if (File.Exists(filePath))
        {
            File.Delete(filePath);    // rimuove file json
            Console.WriteLine("Dipendente rimosso con successo.");
        }
        else
        {
            Console.WriteLine("Dipendente non trovato");
        }
    }

   

     static void SortStipendio()
    {
        // prende in considerazione tutti i file di estensione .json
        var files = Directory.GetFiles(directoryPath, "*.json");

        // creazione di una lista di tipo dynamic permette poi di manipolare gli oggetti deserializzati da JSON 

        List<dynamic> dipendenti = new List<dynamic>();

        //cicla dentro la directory dipendenti scorrendo tutti i file

        foreach (var file in files)
        {

            string jsonRead = File.ReadAllText(file);

            //converte la stringa JSON in un oggetto  
            var dipendente = JsonConvert.DeserializeObject<dynamic>(jsonRead);
            dipendenti.Add(dipendente);
        }

        // algoritmo bubblesort modificato per ordinare il dato dello stipendio in ordine discendente 
        for (int i = 0; i < dipendenti.Count - 1; i++)
        {
            for (int j = 0; j < dipendenti.Count - i - 1; j++)
            {
                if (dipendenti[j].Stipendio < dipendenti[j + 1].Stipendio)
                {
                    var temp = dipendenti[j];
                    dipendenti[j] = dipendenti[j + 1];
                    dipendenti[j + 1] = temp;
                }


            }
        }



        Console.WriteLine("\nDipendenti ordinati per stipendio in ordine discendente:\n");

        foreach (var dipendente in dipendenti)
        {
            Console.WriteLine($"Nome: {dipendente.Nome}");
            Console.WriteLine($"Cognome: {dipendente.Cognome}");
            Console.WriteLine($"Stipendio: {dipendente.Stipendio}");
            Console.WriteLine($"Performance: {dipendente.Performance}");
            Console.WriteLine();
        }
    }




    // metodo per leggere i dati dal json e stamparli
    static void StampaDati(string filePath)
    {
        // legge il contenuto del file json
        string jsonRead = File.ReadAllText(filePath);
        // deserializza la stringa JSON in un oggetto di tipo dynamic
        var dipendente = JsonConvert.DeserializeObject<dynamic>(jsonRead);
        Console.WriteLine($"\nNome: {dipendente.Nome}");
        Console.WriteLine($"Cognome: {dipendente.Cognome}");
        Console.WriteLine($"Data di nascita: {dipendente.DataDiNascita}");
        Console.WriteLine($"Mansione: {dipendente.Mansione}");
        Console.WriteLine($"Stipendio: {dipendente.Stipendio}");
        Console.WriteLine($"Performance: {dipendente.Performance}");
        Console.WriteLine($"Giorni di assenza: {dipendente.Assenze}");
        Console.WriteLine($"Giorni di assenza: {dipendente.Mail}");

    }


    static void TassoDiAssenteismo()
    {
        Console.WriteLine("\nDi seguito l'elenco con il tasso di assenteismo per ogni dipendente su 250 giorni lavorativi equivalente ad 1 anno\n");
        int giorniLavorativiTotali = 250;

        var files = Directory.GetFiles(directoryPath, "*.json");
        List<dynamic> dipendenti = new List<dynamic>();

        foreach (var file in files)
        {

            string jsonRead = File.ReadAllText(file);
            var dipendente = JsonConvert.DeserializeObject<dynamic>(jsonRead);
            dipendenti.Add(dipendente);
        }

        // reverse- modificato la funzione sort in modo da  ordinare i dipendenti dal tasso di assenteismo più alto al più basso

        dipendenti.Sort((y, x) => x.Assenze.CompareTo(y.Assenze));

        foreach (var dipendente in dipendenti)

        {
            int assenze = dipendente.Assenze;
          //  double tassoAssenteismo = ((double)assenze / giorniLavorativiTotali) * 100;
             double assenteismo = ((double)assenze / giorniLavorativiTotali) * 100;     // calcolo del tasso di assenteismo
            double tassoAssenteismo=Math.Round(assenteismo,2);     // calcolo del tasso di assenteismo


            Console.WriteLine($"{dipendente.Nome} {dipendente.Cognome} = {tassoAssenteismo}%\n");

        }



        // Tasso di assenteismo = [(giorni di assenza non giustificate) / (giorni totali di lavoro)] x 100.


    }

}   

```
</details>


# IMPLEMENTAZIONI VERSIONE 4  SENZA SPECTRE CONSOLE   

- Implementazioni funzione GetFile() che consente di aggiungere alla lista dinamica i dipendenti dei file json
- Implementazione funzione IncidenzaPercentuale() per calcolare incidenza dello stipendio in percentuale al fatturato
- Implementazione funzione LeggiJson() legge e  deserializza il json
- Pulizia e refactoring del codice utilizzando le nuove funzioni menzionate per eliminare le ridondanze

<details>
    <summary>Visualizza il codice</summary>

```c#

using Newtonsoft.Json;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;

class Program
{
    static string directoryPath = @"dipendenti/";

    static void Main(string[] args)
    {
        if (!Directory.Exists(directoryPath))
        {
            Directory.CreateDirectory(directoryPath);
        }

        Console.WriteLine("Benvenuto nel programma di gestione del personale.");
        int opzione;

        do
        {
            Console.Clear();
            Console.WriteLine("1. Inserisci dipendente");
            Console.WriteLine("2. Visualizza dipendenti");
            Console.WriteLine("3. Cerca dipendente");
            Console.WriteLine("4. Modifica dipendente");
            Console.WriteLine("5. Rimuovi dipendente");
            Console.WriteLine("6. Tasso di assenteismo");
            Console.WriteLine("7. Indicatore di performance");
            Console.WriteLine("8. Ordina per stipendio");
            Console.WriteLine("9. Incidenza percentuale");
            Console.WriteLine("10. Esci\n");

            opzione = Convert.ToInt32(Console.ReadLine());
            switch (opzione)
            {
                case 1:
                    InserisciDipendente();
                    break;
                case 2:
                    VisualizzaDipendenti();
                    break;
                case 3:
                    CercaDipendente();
                    break;
                case 4:
                    ModificaDipendente();
                    break;
                case 5:
                    RimuoviDipendente();
                    break;
                case 6:
                    TassoDiAssenteismo();
                    break;
                case 7:
                    ValutazionePerformance();
                    break;
                case 8:
                    SortStipendio();
                    break;
                case 9:
                  

                    IncidenzaPercentuale();
                    break;
                case 10:
                    Console.WriteLine("Il programma verrà chiuso. Attendere prego.");
                    break;
                default:
                    Console.WriteLine("Errore di scelta: Prego riprovare");
                    break;
            }

            if (opzione != 10)
            {
                Console.WriteLine("\nPremere un tasto per proseguire");
                Console.ReadKey();
            }
        } while (opzione != 10);
    }

    static void InserisciDipendente()
    {
        do
        {
            try
            {
                Console.WriteLine("Inserisci nome, cognome, data di nascita DD/MM/YYYY, mansione, stipendio, voto performance da 1 a 100, giorni di assenze, email, separati da virgola");
                string? inserimento = Console.ReadLine();
                string[] dati = inserimento.Split(',');

                if (dati.Length != 8)
                {
                    throw new FormatException("L'input deve contenere esattamente otto valori separati da virgola");
                }

                DateTime dataDiNascita = DateTime.ParseExact(dati[2].Trim(), "dd/MM/yyyy", null);
                string dataDiNascitaFormatted = dataDiNascita.ToString("dd/MM/yyyy");

                var dipendente = new
                {
                    Nome = dati[0].Trim(),
                    Cognome = dati[1].Trim(),
                    DataDiNascita = dataDiNascitaFormatted,
                    Mansione = dati[3].Trim(),
                    Stipendio = Convert.ToDecimal(dati[4].Trim()),
                    Performance = Convert.ToInt32(dati[5].Trim()),
                    Assenze = Convert.ToInt32(dati[6].Trim()),
                    Mail = dati[7].Trim()
                };

                string jsonString = JsonConvert.SerializeObject(dipendente, Formatting.Indented);
                string filePath = Path.Combine(directoryPath, $"{dipendente.Nome}_{dipendente.Cognome}.json");
                File.WriteAllText(filePath, jsonString);
            }
            catch (Exception e)
            {
                Console.WriteLine($"ERRORE INSERIMENTO DATI: {e.Message}");
                Console.WriteLine($"CODICE ERRORE: {e.HResult}");
                return;
            }

            Console.WriteLine("Vuoi inserire un altro dipendente? (s/n)");
            string? risposta = Console.ReadLine().Trim().ToLower();

            if (risposta == "n")
            {
                break;
            }
        } while (true);
    }

    static void VisualizzaDipendenti()
    {
        var files = Directory.GetFiles(directoryPath, "*.json");

        if (files.Length > 0)
        {
            Console.WriteLine("Lista dipendenti completa con tutti i dati:\n");
            foreach (var file in files)
            {
                StampaDati(file);
                Console.WriteLine();
            }
        }
        else
        {
            Console.WriteLine("Nessun dipendente nel database.");
        }
    }

    static void CercaDipendente()
    {
        try
        {
            Console.WriteLine("\nInserisci nome e cognome del dipendente che vuoi cercare separati da virgola");
            var inserisciNome = Console.ReadLine();
            var nomi = inserisciNome.Split(',');

            if (nomi.Length != 2)
            {
                throw new FormatException("L'input deve contenere esattamente due valori separati da virgola: nome e cognome.");
            }

            string nome = nomi[0].Trim();
            string cognome = nomi[1].Trim();
            string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

            if (File.Exists(filePath))
            {
                StampaDati(filePath);
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore non trattato: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }

    static void ModificaDipendente()
    {
        try
        {
            Console.WriteLine("\nInserisci nome e cognome del dipendente che vuoi modificare separati da virgola");
            var inserisciNome = Console.ReadLine();
            var nomi = inserisciNome.Split(',');

            if (nomi.Length != 2)
            {
                Console.WriteLine("Nomi non validi. Inserire nome, cognome separati da virgola");
                return;
            }

            string nome = nomi[0].Trim();
            string cognome = nomi[1].Trim();
            string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

            if (File.Exists(filePath))
            {
                var lavoratore = LeggiJson(filePath);

                Console.WriteLine("MODIFICA DIPENDENTE\n1. Cambia nome\n2. Cambia cognome\n3. Cambia data di nascita formato DD/MM/YYYY\n4. Cambia mansione\n5. Cambia stipendio\n6. Cambia punteggio performance\n7. Cambia giorni di assenze\n8. Cambia mail\n9. Esci");
                var scelta = Convert.ToInt32(Console.ReadLine());

                switch (scelta)
                {
                    case 1:
                        Console.WriteLine("Inserisci il nuovo nome");
                        lavoratore.Nome = Console.ReadLine().Trim();
                        break;
                    case 2:
                        Console.WriteLine("Inserisci il nuovo cognome");
                        lavoratore.Cognome = Console.ReadLine().Trim();
                        break;
                    case 3:
                        Console.WriteLine("Inserisci nuova data di nascita");
                        lavoratore.DataDiNascita = DateTime.ParseExact(Console.ReadLine().Trim(), "dd/MM/yyyy", null).ToString("dd/MM/yyyy");
                        break;
                    case 4:
                        Console.WriteLine("Inserisci nuova mansione");
                        lavoratore.Mansione = Console.ReadLine().Trim();
                        break;
                    case 5:
                        Console.WriteLine("Inserisci nuovo stipendio");
                        lavoratore.Stipendio = Convert.ToDecimal(Console.ReadLine());
                        break;
                    case 6:
                        Console.WriteLine("Inserisci nuovo punteggio performance");
                        lavoratore.Performance = Convert.ToInt32(Console.ReadLine());
                        break;
                    case 7:
                        Console.WriteLine("Modifica giorni di assenze");
                        lavoratore.Assenze = Convert.ToInt32(Console.ReadLine());
                        break;
                    case 8:
                        Console.WriteLine("Inserisci il nuovo indirizzo email aziendale");
                        lavoratore.Mail = Console.ReadLine().Trim();
                        break;
                    case 9:
                        Console.WriteLine("\nL'applicazione si sta per chiudere\n");
                        break;
                    default:
                        Console.WriteLine("\nScelta errata. Prego scegliere tra le opzioni disponibili 1-9\n");
                        break;
                }

                string newFilePath = Path.Combine(directoryPath, $"{lavoratore.Nome}_{lavoratore.Cognome}.json");
                string jsonString = JsonConvert.SerializeObject(lavoratore, Formatting.Indented);

                File.Delete(filePath);
                File.WriteAllText(newFilePath, jsonString);

                Console.WriteLine("Dipendente aggiornato con successo.");
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore non trattato: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }

    static void RimuoviDipendente()
    {
        Console.WriteLine("Inserisci nome e cognome del dipendente che vuoi rimuovere separati da virgola");
        var inserisciNome = Console.ReadLine();
        var nomi = inserisciNome.Split(',');

        if (nomi.Length != 2)
        {
            Console.WriteLine("Nomi non validi. Inserire nome, cognome separati da virgola");
            return;
        }

        string nome = nomi[0].Trim();
        string cognome = nomi[1].Trim();
        string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

        try
        {
            if (File.Exists(filePath))
            {
                File.Delete(filePath);
                Console.WriteLine("Dipendente rimosso con successo.");
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore durante la rimozione del dipendente: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }

    static void SortStipendio()
    {
        var dipendenti = GetDipendenti();

        for (int i = 0; i < dipendenti.Count - 1; i++)
        {
            for (int j = 0; j < dipendenti.Count - i - 1; j++)
            {
                if (dipendenti[j].Stipendio < dipendenti[j + 1].Stipendio)
                {
                    var temp = dipendenti[j];
                    dipendenti[j] = dipendenti[j + 1];
                    dipendenti[j + 1] = temp;
                }
            }
        }

        Console.WriteLine("\nDipendenti ordinati per stipendio in ordine discendente:\n");
        foreach (var dipendente in dipendenti)
        {
            Console.WriteLine($"Nome: {dipendente.Nome} {dipendente.Cognome}, Stipendio: {dipendente.Stipendio}, Performance: {dipendente.Performance}");
        }
    }

    static void StampaDati(string filePath)
    {
        string jsonRead = File.ReadAllText(filePath);
        var dipendente = JsonConvert.DeserializeObject<dynamic>(jsonRead);
        Console.WriteLine($"\nNome: {dipendente.Nome}");
        Console.WriteLine($"Cognome: {dipendente.Cognome}");
        Console.WriteLine($"Data di nascita: {dipendente.DataDiNascita}");
        Console.WriteLine($"Mansione: {dipendente.Mansione}");
        Console.WriteLine($"Stipendio: {dipendente.Stipendio}");
        Console.WriteLine($"Performance: {dipendente.Performance}");
        Console.WriteLine($"Giorni di assenza: {dipendente.Assenze}");
        Console.WriteLine($"Mail aziendale: {dipendente.Mail}");
    }

    static void TassoDiAssenteismo()
    {
        Console.WriteLine("\nDi seguito l'elenco con il tasso di assenteismo per ogni dipendente su 250 giorni lavorativi equivalente ad 1 anno\n");
        int giorniLavorativiTotali = 250;

        try
        {
            var dipendenti = GetDipendenti();

            foreach (var dipendente in dipendenti)
            {
                int assenze = dipendente.Assenze;
                double assenteismo = ((double)assenze / giorniLavorativiTotali) * 100;
                double tassoAssenteismo = Math.Round(assenteismo, 2);

                Console.WriteLine($"{dipendente.Nome} {dipendente.Cognome}, Tasso di assenteismo: {tassoAssenteismo}%");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore generale: {e.Message}");
        }
    }

    static void ValutazionePerformance()
    {
        var dipendenti = GetDipendenti();

        Console.WriteLine("\nDivide i dipendendenti in 2 gruppi in base al rendimento");

        for (int i = 0; i < dipendenti.Count - 1; i++)
        {
            for (int j = 0; j < dipendenti.Count - i - 1; j++)
            {
                if (dipendenti[j].Performance < dipendenti[j + 1].Performance)
                {
                    var temp = dipendenti[j];
                    dipendenti[j] = dipendenti[j + 1];
                    dipendenti[j + 1] = temp;
                }
            }
        }

        int split = dipendenti.Count / 2;
        List<dynamic> squadra1 = dipendenti.GetRange(0, split);
        List<dynamic> squadra2 = dipendenti.GetRange(split, dipendenti.Count - split);

        Console.WriteLine("\nGruppo con le performance più alte:\n");
        foreach (var impiegato in squadra1)
        {
            Console.WriteLine($"Nome: {impiegato.Nome} {impiegato.Cognome}, Performance: {impiegato.Performance}");
        }

        Console.WriteLine("\nGruppo con le performance più basse:\n");
        foreach (var impiegato in squadra2)
        {
            Console.WriteLine($"Nome: {impiegato.Nome} {impiegato.Cognome}, Performance: {impiegato.Performance}");
        }

        squadra2.Sort((x, y) => x.Performance.CompareTo(y.Performance));
        int index = (15 * squadra2.Count) / 100;

        if (index == 0 && squadra2.Count > 0)
        {
            index = 1;
        }

        Console.WriteLine("\nDi seguito il 15% delle performance peggiori\n");
        for (int i = 0; i < index; i++)
        {
            var membro = squadra2[i];
            Console.WriteLine($"Nome: {membro.Nome} {membro.Cognome}, Performance: {membro.Performance}");
        }
    }

    static List<dynamic> GetDipendenti()
    {
        var files = Directory.GetFiles(directoryPath, "*.json");
        List<dynamic> dipendenti = new List<dynamic>();

        foreach (var file in files)
        {
            var dipendente = LeggiJson(file);
            dipendenti.Add(dipendente);
        }

        return dipendenti;
    }

    static dynamic LeggiJson(string filePath)
    {
        string jsonRead = File.ReadAllText(filePath);
        return JsonConvert.DeserializeObject<dynamic>(jsonRead);
    }

    static void IncidenzaPercentuale()
{
    string fileTxt = "fatturato.txt";
    double fatturato;

    if (!File.Exists(fileTxt))
    {
        Console.WriteLine("Inserisci fatturato");
        fatturato = Convert.ToDouble(Console.ReadLine());
        File.WriteAllText(fileTxt, fatturato.ToString());
    }
    else
    {
        string[] lines = File.ReadAllLines(fileTxt);
        if (lines.Length == 0)
        {
            Console.WriteLine("Inserisci fatturato");
            fatturato = Convert.ToDouble(Console.ReadLine());
            File.WriteAllText(fileTxt, fatturato.ToString());
        }
        else
        {
            fatturato = Convert.ToDouble(lines[0]);
        }
    }

    var dipendenti = GetDipendenti();

    dipendenti.Sort((y, x) => x.Stipendio.CompareTo(y.Stipendio));

    Console.WriteLine("\nDipendenti e incidenza stipendio lordo sul fatturato:\n");
   

    foreach (var dipendente in dipendenti)
    {
        double stipendio = Convert.ToDouble(dipendente.Stipendio);
        double costoPersonale = (stipendio / fatturato) * 100;
        double costoPercentuale = Math.Round(costoPersonale, 2);

        Console.WriteLine($"Nome:{dipendente.Nome}\nCognome:{dipendente.Cognome}\nData di nascita:{dipendente.DataDiNascita}\nMansione:{dipendente.Mansione}\nStipendio:{dipendente.Stipendio}\nRapporto stipendio/fatturato:{costoPercentuale}%\nPerformance:{dipendente.Performance}\nAssenze:{dipendente.Assenze}");
    }
}

}

```

</details>


# IMPLEMENTAZIONI VERSIONE 5 CON SPECTRE CONSOLE

- implementazione di Spectre console per rendere il menu principale user friendly e interattivo

- Creazione di un sottomenu in modo analogo al menu principale per poter scegliere il singolo campo del dipendente da modificare

- Aggiunta funzione CreaTabella() per creare e ordinare i dati in tabella

- Aggiunta funzione CreaColonne() per non ripetere il processo di creazione delle colonne all'interno di ogni funzione


<details>
    <summary>Visualizza il codice</summary>

 ```c#

using Newtonsoft.Json;
using Spectre.Console;

class Program
{

    // crea cartella dipendenti dove verranno messi i file json per ogni dipendente
    static string directoryPath = @"dipendenti/";

    static void Main(string[] args)

    {
        // se la cartella non esiste la crea

        if (!Directory.Exists(directoryPath))
        {
            Directory.CreateDirectory(directoryPath);
        }

        Console.WriteLine("Benvenuto nel programma di gestione del personale.");

        // variabile per il menu di spectre console
        var opzione = "";

        do
        {
            Console.Clear();

            // creazione del menu con spectre console
            opzione = AnsiConsole.Prompt(
         new SelectionPrompt<string>()
        .Title("GESTIONALE PERSONALE")
        .PageSize(9)
        .MoreChoicesText("[grey](Move up and down to reveal more)[/]")
        .AddChoices(new[] {
            "Inserisci dipendente","Visualizza dipendenti","Cerca dipendente",
            "Modifica dipendente","Rimuovi dipendente","Tasso di assenteismo","Valutazione performance","Ordina stipendi","Rapporto stipendio fatturato","Esci",
        }));


            // scelta del tipo di azione da svolgere


            switch (opzione)
            {
                case "Inserisci dipendente":
                    InserisciDipendente();
                    break;
                case "Visualizza dipendenti":
                    VisualizzaDipendenti();
                    break;
                case "Cerca dipendente":
                    CercaDipendente();
                    break;
                case "Modifica dipendente":
                    ModificaDipendente();
                    break;
                case "Rimuovi dipendente":
                    RimuoviDipendente();
                    break;
                case "Tasso di assenteismo":
                    TassoDiAssenteismo();
                    break;
                case "Valutazione performance":

                    ValutazionePerformance();
                    break;
                case "Ordina stipendi":

                    SortStipendio();
                    break;
                case "Rapporto stipendio fatturato":

                    IncidenzaPercentuale();
                    break;
                case "Esci":
                    Console.WriteLine("Il programma verrà chiuso. Attendere prego.");
                    break;
                default:
                    Console.WriteLine("Errore di scelta: Prego riprovare");
                    break;
            }

            // se viene scelta l'opzione 9 il programma si chiude altrimenti prosegue

            if (opzione != "Esci")
            {
                Console.WriteLine("\nPremere un tasto per proseguire");
                Console.ReadKey();
            }

        } while (opzione != "Esci");
    }

    // funzione per inserire i dati del dipendente e creare il relativo json

    static void InserisciDipendente()
    {
        do
        {
            try
            {

                Console.WriteLine("Inserisci nome, cognome, data di nascita DD/MM/YYYY,mansione, stipendio,voto performance da 1 a 100 ,giorni di assenze,email,separate da virgola");

                // accetta l'input dei dati da console
                string? inserimento = Console.ReadLine();

                // permette l'inserimento di più valori divisi dalla virgola

                string[] dati = inserimento.Split(',');

                if (dati.Length != 8)
                {
                    throw new FormatException("L'input deve contenere esattamente otto valori separati da virgola");
                }

                // formattazione data di nascita
                //ParseExact permette di specificare esattamente come vogliamo il formato  della data converte da stringa a oggetto Datetime

                DateTime dataDiNascita = DateTime.ParseExact(dati[2].Trim(), "dd/MM/yyyy", null);

                //viene riconvertito in stringa
                string dataDiNascitaFormatted = dataDiNascita.ToString("dd/MM/yyyy");

                //  creazione di un oggetto dipendente contenente i dati richiesti dall'applicazione
                var dipendente = new
                {
                    Nome = dati[0].Trim(),
                    Cognome = dati[1].Trim(),
                    DataDiNascita = dataDiNascitaFormatted, //DateTime.Parse(dati[2].Trim()),
                    Mansione = dati[3].Trim(),
                    Stipendio = Convert.ToDecimal(dati[4].Trim()),
                    Performance = Convert.ToInt32(dati[5].Trim()),
                    Assenze = Convert.ToInt32(dati[6].Trim()),
                    Mail = dati[7].Trim()
                };

                // serializza l'oggetto in una stringa Json e lo indenta per renderlo più leggibile

                string jsonString = JsonConvert.SerializeObject(dipendente, Formatting.Indented);

                // Path.Combine concatena il path della cartella dipendenti al path dei file json di ogni dipendente
                string filePath = Path.Combine(directoryPath, $"{dipendente.Nome}_{dipendente.Cognome}.json");

                //scrive il file

                File.WriteAllText(filePath, jsonString);
            }

            catch (Exception e)
            {
                Console.WriteLine($"ERRORE INSERIMENTO DATI: {e.Message}");     // messaggio eccezione
                Console.WriteLine($"CODICE ERRORE:{e.HResult}");                //codice numerico eccezione
                return;
            }


            // se si svuole terminare l'immissione della registrazione del dipendente basta digitare n

            Console.WriteLine("Vuoi inserire un altro dipendente? (s/n)");
            string? risposta = Console.ReadLine().Trim().ToLower();

            if (risposta == "n")
            {
                break;
            }
        } while (true);


    }
    // funzione per visualizzare tutti i dipendenti con le relative caratteristiche
    static void VisualizzaDipendenti()
    {
        // analizza tutti i file con estensione .json dentro la directoryPath(cartella dipendenti)
        var files = Directory.GetFiles(directoryPath, "*.json");  //

        // verifica se c'è almeno un file per eseguire il codice
        if (files.Length > 0)
        {
            Console.WriteLine("Lista dipendenti completa con tutti i dati:\n");

            // creazione tabella dipendenti
      

            var table = CreaColonne(new string[]{"Nome","Cognome","Data di nascita","Mansione","Stipendio annuale","Performance","Giorni di assenza","Email aziendale"});


            // aggiunge nella tabella i dati di tutti i dipendenti presi dai json

            foreach (var file in files)
            {


                var dipendente = LeggiJson(file);


                table.AddRow($"{dipendente.Nome}", $"{dipendente.Cognome}", $"{dipendente.DataDiNascita}", $"{dipendente.Mansione}", $"{dipendente.Stipendio}", $"{dipendente.Performance}", $"{dipendente.Assenze}", $"{dipendente.Mail}");


            }
            var final = files.AsEnumerable().OrderBy(x => x[0]);
            AnsiConsole.Write(table);
        }
        else
        {
            Console.WriteLine("Nessun dipendente nel database.");
        }
    }

    // metodo per cercare il dipendente inserendo nome,cognome
    static void CercaDipendente()
    {
        try
        {
            Console.WriteLine("\nInserisci nome e cognome del dipendente che vuoi cercare separati da virgola");
            var inserisciNome = Console.ReadLine();

            // permette l'inserimento di molteplici input separati dalla virgola quindi permette un array di stringhe con nome cognome
            var nomi = inserisciNome.Split(',');

            // il dipendente deve essere cercato inserendo nome,cognome se vengono inseriti più valori viene gestito l'errore


            if (nomi.Length != 2)
            {
                throw new FormatException("L'input deve contenere esattamente due valori separati da virgola: nome e cognome.");

            }

            // creato variabili per associarvi il valore di nome e cognome relativi all'array nomi

            string nome = nomi[0].Trim();
            string cognome = nomi[1].Trim();

            // nome e cognome di ogni dipendente diventerenno il rispettivo nome dei file json 
            string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

            // verifica se un file json esiste

            if (File.Exists(filePath))
            {

                // StampaDati(filePath);
                var table = CreaTabella(filePath);
                AnsiConsole.Write(table);
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore non trattato: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }

    //cerca dipendente per nome,cognome e poi modifica le caratteristiche del dipendente a scelta

    static void ModificaDipendente()
    {

        try
        {
            Console.WriteLine("\nInserisci nome e cognome del dipendente che vuoi modificare separati da virgola");

            var inserisciNome = Console.ReadLine();
            var nomi = inserisciNome.Split(',');

            // il dipendente va cercato solo inserendo nome,cognome

            if (nomi.Length != 2)
            {
                Console.WriteLine("Nomi non validi.Inserire nome,cognome separati da virgola");
                return;
            }

            // Trim() rimuove gli spazi vuoti dal nome e cognome

            string nome = nomi[0].Trim();
            string cognome = nomi[1].Trim();
            string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

            if (File.Exists(filePath))
            {

                var lavoratore = LeggiJson(filePath);
                var inserimento = "";

                // sottomenu per scegliere il valore da modificare

                inserimento = AnsiConsole.Prompt(
           new SelectionPrompt<string>()
          .Title("MODIFICA DIPENDENTE")
          .PageSize(8)
          .MoreChoicesText("[grey](Move up and down to reveal more)[/]")
          .AddChoices(new[] {
            "Cambia nome","Cambia cognome","Cambia data di nascita formato DD/MM/YYYY",
            "Cambia mansione","Cambia stipendio","Cambia punteggio performance","Cambia giorni di assenze","Cambia mail","Esci",
          }));



                switch (inserimento)
                {


                    case "Cambia nome":

                        Console.WriteLine("Inserici il nuovo nome");
                        lavoratore.Nome = Console.ReadLine().Trim();



                        break;

                    case "Cambia cognome":
                        Console.WriteLine("Inserici il nuovo cognome");
                        lavoratore.Cognome = Console.ReadLine().Trim();


                        break;

                    case "Cambia data di nascita formato DD/MM/YYYY":
                        Console.WriteLine("Inserisci nuova data di nascita");
                        lavoratore.DataDiNascita = DateTime.ParseExact(Console.ReadLine().Trim(), "dd/MM/yyyy", null).ToString("dd/MM/yyyy");

                        break;

                    case "Cambia mansione":
                        Console.WriteLine("Inserisci nuova mansione");
                        lavoratore.Mansione = Console.ReadLine().Trim();


                        break;

                    case "Cambia stipendio":
                        Console.WriteLine("Inserisci nuovo stipendio");
                        lavoratore.Stipendio = Convert.ToDecimal(Console.ReadLine());

                        break;

                    case "Cambia punteggio performance":
                        Console.WriteLine("Inserisci nuovo punteggio performance");
                        lavoratore.Performance = Convert.ToInt32(Console.ReadLine());

                        break;

                    case "Cambia giorni di assenze":
                        Console.WriteLine("Modifica giorni di assenze");
                        lavoratore.Assenze = Convert.ToInt32(Console.ReadLine());

                        break;

                    case "Cambia mail":
                        Console.WriteLine("Inserisci il nuovo indirizzo email aziendale");
                        lavoratore.Mail = Console.ReadLine().Trim();


                        break;

                    case "Esci":
                        Console.WriteLine("\nL'applicazione si sta per chiudere\n");

                        break;

                    default:
                        Console.WriteLine("\nScelta errata.Prego scegliere tra le opzioni disponibili 1-8\n");
                        break;
                }

                // se nome,cognome vengono modificati cambia anche il nome del json corrispondente

                string newFilePath = Path.Combine(directoryPath, $"{lavoratore.Nome}_{lavoratore.Cognome}.json");

                // Serializza i dati aggiornati del dipendente 
                string jsonString = JsonConvert.SerializeObject(lavoratore, Formatting.Indented);

                //Cancella il vecchio json

                File.Delete(filePath);

                //scrive il nuovo file json con i dati aggiornati serializzati

                File.WriteAllText(newFilePath, jsonString);


                Console.WriteLine("Dipendente aggiornato con successo.");
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore non trattato: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }

    // metodo per rimuovere il dipendente e il relativo file json inserendo nome,cognome nella console
    static void RimuoviDipendente()
    {

        Console.WriteLine("Inserisci nome e cognome del dipendente che vuoi rimuovere separati da virgola");
        var inserisciNome = Console.ReadLine();
        var nomi = inserisciNome.Split(',');

        if (nomi.Length != 2)
        {
            Console.WriteLine("Nomi non validi.Inserire nome,cognome separati da virgola");
            return;
        }

        string nome = nomi[0].Trim();
        string cognome = nomi[1].Trim();
        string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

        try
        {

            if (File.Exists(filePath))
            {
                File.Delete(filePath);    // rimuove file json
                Console.WriteLine("Dipendente rimosso con successo.");
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore durante la rimozione del dipendente: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }



    //metodo per ordinare gli stipendi dal più alto al più basso e vedere alcuni  dati del dipendente

    static void SortStipendio()
    {
        var dipendenti = GetDipendenti();

        // algoritmo bubblesort modificato per ordinare il dato dello stipendio in ordine discendente 
        for (int i = 0; i < dipendenti.Count - 1; i++)
        {
            for (int j = 0; j < dipendenti.Count - i - 1; j++)
            {
                if (dipendenti[j].Stipendio < dipendenti[j + 1].Stipendio)
                {
                    var temp = dipendenti[j];
                    dipendenti[j] = dipendenti[j + 1];
                    dipendenti[j + 1] = temp;
                }


            }
        }


        var table = CreaColonne(new string[]{"Dipendente","Stipendio","Performance"});


        Console.WriteLine("\nDipendenti ordinati per stipendio in ordine discendente:\n");

        foreach (var dipendente in dipendenti)
        {
            table.AddRow($"{dipendente.Nome} {dipendente.Cognome}", $"{dipendente.Stipendio}", $"{dipendente.Performance}");

        }

        AnsiConsole.Write(table);
    }




    // metodo per leggere i dati dal json e stamparli
    static void StampaDati(string filePath)
    {
        // legge il contenuto del file json
        string jsonRead = File.ReadAllText(filePath);
        // deserializza la stringa JSON in un oggetto di tipo dynamic
        var dipendente = JsonConvert.DeserializeObject<dynamic>(jsonRead);
        Console.WriteLine($"\nNome: {dipendente.Nome}");
        Console.WriteLine($"Cognome: {dipendente.Cognome}");
        Console.WriteLine($"Data di nascita: {dipendente.DataDiNascita}");
        Console.WriteLine($"Mansione: {dipendente.Mansione}");
        Console.WriteLine($"Stipendio: {dipendente.Stipendio}");
        Console.WriteLine($"Performance: {dipendente.Performance}");
        Console.WriteLine($"Giorni di assenza: {dipendente.Assenze}");
        Console.WriteLine($"Mail aziendale: {dipendente.Mail}");


    }

    // meotodo che calcola il tasso di assenteismo su un totale di 250 giorni lavorativi l'anno
    static void TassoDiAssenteismo()
    {
        Console.WriteLine("\nDi seguito l'elenco con il tasso di assenteismo per ogni dipendente su 250 giorni lavorativi equivalente ad 1 anno\n");
        int giorniLavorativiTotali = 250;

        try
        {
            var dipendenti = GetDipendenti();


            // tabella 

            var table = CreaColonne(new string[]{"Dipendente","Tasso di assenteismo"});


            // reverse- modificato la funzione sort in modo da  ordinare i dipendenti dal tasso di assenteismo più alto al più basso

            dipendenti.Sort((y, x) => x.Assenze.CompareTo(y.Assenze));

            foreach (var dipendente in dipendenti)

            {
                int assenze = dipendente.Assenze;


                double assenteismo = ((double)assenze / giorniLavorativiTotali) * 100;     // calcolo del tasso di assenteismo
                double tassoAssenteismo = Math.Round(assenteismo, 2);

                table.AddRow($"{dipendente.Nome} {dipendente.Cognome}", $"{tassoAssenteismo}%");


            }

            AnsiConsole.Write(table);

            // Tasso di assenteismo = [(giorni di assenza non giustificate) / (giorni totali di lavoro)] x 100.


        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore generale: {e.Message}");
        }

    }

    //metodo che  legge il file json e lo deserializza
    static dynamic LeggiJson(string filePath)
    {

        string jsonRead = File.ReadAllText(filePath);
        return JsonConvert.DeserializeObject<dynamic>(jsonRead);
    }

    // metodo per ordinare i dipendenti in base alle performance dividendoli in 2 gruppi in base al punteggio 
    static void ValutazionePerformance()
    {
       var dipendenti =GetDipendenti();

        Console.WriteLine("\nDivide i dipendendenti in 2 gruppi in base al rendimento");

        // ordina dipendenti per performance

        for (int i = 0; i < dipendenti.Count - 1; i++)
        {
            for (int j = 0; j < dipendenti.Count - i - 1; j++)
            {
                if (dipendenti[j].Performance < dipendenti[j + 1].Performance)
                {
                    var temp = dipendenti[j];
                    dipendenti[j] = dipendenti[j + 1];
                    dipendenti[j + 1] = temp;
                }

            }

        }

        // divide i dipendenti in 2 gruppi.Nel primo vengono inseriti quelli con le performance migliori

        int split = dipendenti.Count / 2;
        List<dynamic> squadra1 = dipendenti.GetRange(0, split);
        List<dynamic> squadra2 = dipendenti.GetRange(split, dipendenti.Count - split);

        // aggiunto tabella dipendenti con performance migliori


       var table =  CreaColonne(new string[]{"Dipendente","Performance"});

        // aggiunto tabella dipendenti con performance inferiori

        var table2 =  CreaColonne(new string[]{"Dipendente","Performance"});

        // aggiunto tabella dipendenti con performance inferiori gli ultimi 15%


        var table3 = CreaColonne(new string[]{"Dipendente","Performance"});


        // aggiunge nella tabella i dati del dipendente mettendo in evidenza le performance
        // in squadra1 vengono messi i migliori

        foreach (var impiegato in squadra1)
        {
            table.AddRow($"{impiegato.Nome} {impiegato.Cognome}", $"{impiegato.Performance}");


        }


        foreach (var impiegato in squadra2)
        {
            table2.AddRow($"{impiegato.Nome} {impiegato.Cognome}", $"{impiegato.Performance}");


        }


        Console.WriteLine("\nGruppo con le performance più alte:\n");

        AnsiConsole.Write(table);
        Console.WriteLine("\nGruppo con le performance più basse:\n");
        AnsiConsole.Write(table2);

        // ordina i valori


        squadra2.Sort((x, y) => x.Performance.CompareTo(y.Performance));

        // formula per trovare il 15% dei risultati più bassi

        int index = (15 * squadra2.Count) / 100;

        // Se il 15% è 0.5 o più, arrotonda per eccesso a 1
        if (index == 0 && squadra2.Count > 0)
        {
            index = 1;
        }

        // stampa il 15% dei risultati peggiori

        for (int i = 0; i < index; i++)
        {
            var membro = squadra2[i];
            table3.AddRow($"{membro.Nome} {membro.Cognome}", $"Performance: {membro.Performance}\n");
        }

        Console.WriteLine("\nDi seguito il 15% delle performance peggiori\n");
        AnsiConsole.Write(table3);

    }

    // funzione che calcola l'incidenza percentuale dello stipendio in rapporto al fatturato
    static void IncidenzaPercentuale()
    {
        string fileTxt = "fatturato.txt";

        double fatturato;

        if (!File.Exists(fileTxt))
        {
            Console.WriteLine("Inserisci fatturato");
            fatturato = Convert.ToDouble(Console.ReadLine());
            File.WriteAllText(fileTxt, fatturato.ToString());




        }
        else
        {
            string[] lines = File.ReadAllLines(fileTxt);
            if (lines.Length == 0)
            {
                // Se il file è vuoto o il contenuto non è valido, chiede il fatturato all'utente
                Console.WriteLine("Inserisci fatturato");
                //converte fatturato in decimale
                fatturato = Convert.ToDouble(Console.ReadLine());
                //scrive valori sul file txt convertendolo in stringa
                File.WriteAllText(fileTxt, fatturato.ToString());
            }
            else
            {
                fatturato = Convert.ToDouble(lines[0]);     // converte in double per i calcoli
            }
        }


        var dipendenti = GetDipendenti();

           // creazione tabella 

        var table =CreaColonne(new string[]{"Nome","Cognome","Data di nascita","Mansione","Stipendio","Incidenza stipendio lordo sul fatturato","Performance","Giorni di assenze"});

        dipendenti.Sort((y, x) => x.Stipendio.CompareTo(y.Stipendio));

        foreach (var dipendente in dipendenti)

        {
            double stipendio = Convert.ToDouble(dipendente.Stipendio);

            //formula Incidenza percentuale : (Cifra Inferiore / Cifra Superiore) X 100

            double costoPersonale = (stipendio / fatturato) * 100;     // calcolo del tasso d'incidenza
            double costoPercentuale = Math.Round(costoPersonale, 2);   // limite 2 cifre decimali

            //Console.WriteLine($"{dipendente.Nome} {dipendente.Cognome} {dipendente.Stipendio} {costoPercentuale}% {dipendente.Performance}");
            table.AddRow($"{dipendente.Nome}", $"{dipendente.Cognome}", $"{dipendente.DataDiNascita}", $"{dipendente.Mansione}", $"{dipendente.Stipendio}", $"{costoPercentuale}%", $"{dipendente.Performance}", $"{dipendente.Assenze}");

        }
        AnsiConsole.Write(table);
    }

// metodo che consente di aggiungere alla lista dinamica i dipendenti dei file json
    static List<dynamic> GetDipendenti()
{
    // prende in considerazione tutti i file di estensione .json

    var files = Directory.GetFiles(directoryPath, "*.json");
     // creazione di una lista di tipo dynamic permette poi di manipolare gli oggetti deserializzati da JSON 
    List<dynamic> dipendenti = new List<dynamic>();
      //cicla dentro la directory dipendenti scorrendo tutti i file e aggiungendo i dipendenti alla lista

    foreach (var file in files)
    {
        var dipendente = LeggiJson(file);
        dipendenti.Add(dipendente);
    }

    return dipendenti;
}
    // metodo per creare la tabella con spectre console in modo da visualizzare tutti i dati del dipendente
    static dynamic CreaTabella(string filePath)
    {
         var dipendente = LeggiJson(filePath);

        var table = new Table();
        table.Border(TableBorder.Square);


    
        table.AddColumn("Nome");
        table.AddColumn("Cognome");
        table.AddColumn("Data di nascita");
        table.AddColumn("Mansione");
        table.AddColumn("Stipendio");
        table.AddColumn("Performance");
        table.AddColumn("Giorni di assenza");
        table.AddColumn("Email aziendale");


        table.AddRow($"{dipendente.Nome}", $"{dipendente.Cognome}", $"{dipendente.DataDiNascita}", $"{dipendente.Mansione}", $"{dipendente.Stipendio}", $"{dipendente.Performance}", $"{dipendente.Assenze}", $"{dipendente.Mail}");


        return table;
    }

    static Table CreaColonne(string[]colonne){
        var table = new Table().Border(TableBorder.Square);

        foreach(string colonna in colonne){
            table.AddColumn(new TableColumn(colonna).Centered());

        }
        return table;
    }


}



```

</details>

# IMPLEMENTAZIONE 6 VERSIONE FINALE CON SPECTRE

- Aggiunta funzione GetNomeCognome() per gestire in modo più efficiente l'input di nome,cognome nelle verie funzioni del programma
- Modificata funzione CreaTabella
- Aggiungere timestamp nel nome del file per discriminare i json in caso di stesso nome e cognome

<details>
    <summary>Visualizza il codice</summary>

 ```c#

 using Newtonsoft.Json;
using Spectre.Console;

class Program
{

    // crea cartella dipendenti dove verranno messi i file json per ogni dipendente
    static string directoryPath = @"dipendenti/";

    static void Main(string[] args)

    {
        // se la cartella non esiste la crea

        if (!Directory.Exists(directoryPath))
        {
            Directory.CreateDirectory(directoryPath);
        }

        Console.WriteLine("Benvenuto nel programma di gestione del personale.");

        // variabile per il menu di spectre console
        var opzione = "";

        do
        {
            Console.Clear();

            // creazione del menu con spectre console
            opzione = AnsiConsole.Prompt(
         new SelectionPrompt<string>()
        .Title("GESTIONALE PERSONALE")
        .PageSize(9)
        .MoreChoicesText("[grey](Move up and down to reveal more)[/]")
        .AddChoices(new[] {
            "Inserisci dipendente","Visualizza dipendenti","Cerca dipendente",
            "Modifica dipendente","Rimuovi dipendente","Tasso di assenteismo","Valutazione performance","Ordina stipendi","Rapporto stipendio fatturato","Esci",
        }));

            // scelta del tipo di azione da svolgere

            switch (opzione)
            {
                case "Inserisci dipendente":
                    InserisciDipendente();
                    break;
                case "Visualizza dipendenti":
                    VisualizzaDipendenti();
                    break;
                case "Cerca dipendente":
                    CercaDipendente();
                    break;
                case "Modifica dipendente":
                    ModificaDipendente();
                    break;
                case "Rimuovi dipendente":
                    RimuoviDipendente();
                    break;
                case "Tasso di assenteismo":
                    TassoDiAssenteismo();
                    break;
                case "Valutazione performance":

                    ValutazionePerformance();
                    break;
                case "Ordina stipendi":

                    SortStipendio();
                    break;
                case "Rapporto stipendio fatturato":

                    IncidenzaPercentuale();
                    break;
                case "Esci":
                    Console.WriteLine("Il programma verrà chiuso. Attendere prego.");
                    break;
                default:
                    Console.WriteLine("Errore di scelta: Prego riprovare");
                    break;
            }

            // se viene scelta l'opzione 9 il programma si chiude altrimenti prosegue

            if (opzione != "Esci")
            {
                Console.WriteLine("\nPremere un tasto per proseguire");
                Console.ReadKey();
            }

        } while (opzione != "Esci");
    }

    // funzione per inserire i dati del dipendente e creare il relativo json

    static void InserisciDipendente()
    {
        do
        {
            try
            {

                Console.WriteLine("Inserisci nome, cognome, data di nascita DD/MM/YYYY,mansione, stipendio,voto performance da 1 a 100 ,giorni di assenze,email,separate da virgola\n");

                // accetta l'input dei dati da console
                string? inserimento = Console.ReadLine();

                // permette l'inserimento di più valori divisi dalla virgola

                string[] dati = inserimento.Split(',');

                if (dati.Length != 8)
                {
                    throw new FormatException("L'input deve contenere esattamente otto valori separati da virgola");
                }

                // formattazione data di nascita
                //ParseExact permette di specificare esattamente come vogliamo il formato  della data converte da stringa a oggetto Datetime

                DateTime dataDiNascita = DateTime.ParseExact(dati[2].Trim(), "dd/MM/yyyy", null);

                //viene riconvertito in stringa
                string dataDiNascitaFormatted = dataDiNascita.ToString("dd/MM/yyyy");

                //  creazione di un oggetto dipendente contenente i dati richiesti dall'applicazione
                var dipendente = new
                {
                    Nome = dati[0].Trim(),
                    Cognome = dati[1].Trim(),
                    DataDiNascita = dataDiNascitaFormatted, //DateTime.Parse(dati[2].Trim()),
                    Mansione = dati[3].Trim(),
                    Stipendio = Convert.ToDecimal(dati[4].Trim()),
                    Performance = Convert.ToInt32(dati[5].Trim()),
                    Assenze = Convert.ToInt32(dati[6].Trim()),
                    Mail = dati[7].Trim()
                };

                // serializza l'oggetto in una stringa Json e lo indenta per renderlo più leggibile

                string jsonString = JsonConvert.SerializeObject(dipendente, Formatting.Indented);

                // Path.Combine concatena il path della cartella dipendenti al path dei file json di ogni dipendente
                string filePath = Path.Combine(directoryPath, $"{dipendente.Nome}_{dipendente.Cognome}.json");

                //scrive il file

                File.WriteAllText(filePath, jsonString);
            }

            catch (Exception e)
            {
                Console.WriteLine($"ERRORE INSERIMENTO DATI: {e.Message}");     // messaggio eccezione
                Console.WriteLine($"CODICE ERRORE:{e.HResult}");                //codice numerico eccezione
                return;
            }


            // se si svuole terminare l'immissione della registrazione del dipendente basta digitare n

            Console.WriteLine("Vuoi inserire un altro dipendente? (s/n)");
            string? risposta = Console.ReadLine().Trim().ToLower();

            if (risposta == "n")
            {
                break;
            }
        } while (true);


    }
    // funzione per visualizzare tutti i dipendenti con le relative caratteristiche
    static void VisualizzaDipendenti()
    {
        // analizza tutti i file con estensione .json dentro la directoryPath(cartella dipendenti)
        var files = Directory.GetFiles(directoryPath, "*.json");  //

        // verifica se c'è almeno un file per eseguire il codice
        if (files.Length > 0)
        {
            Console.WriteLine("Lista dipendenti completa con tutti i dati:\n");

            // creazione tabella dipendenti
      

            var table = CreaColonne(new string[]{"Nome","Cognome","Data di nascita","Mansione","Stipendio annuale","Performance","Giorni di assenza","Email aziendale"});


            // aggiunge nella tabella i dati di tutti i dipendenti presi dai json

            foreach (var file in files)
            {


                var dipendente = LeggiJson(file);


                table.AddRow($"{dipendente.Nome}", $"{dipendente.Cognome}", $"{dipendente.DataDiNascita}", $"{dipendente.Mansione}", $"{dipendente.Stipendio}", $"{dipendente.Performance}", $"{dipendente.Assenze}", $"{dipendente.Mail}");


            }
            var final = files.AsEnumerable().OrderBy(x => x[0]);
            AnsiConsole.Write(table);
        }
        else
        {
            Console.WriteLine("Nessun dipendente nel database.");
        }
    }

    // metodo per cercare il dipendente inserendo nome,cognome
    static void CercaDipendente()
    {
        try
        {
            Console.Clear();
          
            GetNomeCognome(out string nome, out string cognome);
            
            // nome e cognome di ogni dipendente diventerenno il rispettivo nome dei file json 
            string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

            // verifica se un file json esiste

            if (File.Exists(filePath))
            {

                // StampaDati(filePath);
                var table = CreaTabella(filePath);
                AnsiConsole.Write(table);
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore non trattato: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }

    //cerca dipendente per nome,cognome e poi modifica le caratteristiche del dipendente a scelta

    static void ModificaDipendente()
    {

        try
        {
          GetNomeCognome(out string nome, out string cognome);
            string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

            if (File.Exists(filePath))
            {

                var lavoratore = LeggiJson(filePath);
                var inserimento = "";

                // sottomenu per scegliere il valore da modificare

                inserimento = AnsiConsole.Prompt(
           new SelectionPrompt<string>()
          .Title("MODIFICA DIPENDENTE")
          .PageSize(8)
          .MoreChoicesText("[grey](Move up and down to reveal more)[/]")
          .AddChoices(new[] {
            "Cambia nome","Cambia cognome","Cambia data di nascita formato DD/MM/YYYY",
            "Cambia mansione","Cambia stipendio","Cambia punteggio performance","Cambia giorni di assenze","Cambia mail","Esci",
          }));



                switch (inserimento)
                {


                    case "Cambia nome":

                        Console.WriteLine("Inserici il nuovo nome");
                        lavoratore.Nome = Console.ReadLine().Trim();



                        break;

                    case "Cambia cognome":
                        Console.WriteLine("Inserici il nuovo cognome");
                        lavoratore.Cognome = Console.ReadLine().Trim();


                        break;

                    case "Cambia data di nascita formato DD/MM/YYYY":
                        Console.WriteLine("Inserisci nuova data di nascita");
                        lavoratore.DataDiNascita = DateTime.ParseExact(Console.ReadLine().Trim(), "dd/MM/yyyy", null).ToString("dd/MM/yyyy");

                        break;

                    case "Cambia mansione":
                        Console.WriteLine("Inserisci nuova mansione");
                        lavoratore.Mansione = Console.ReadLine().Trim();


                        break;

                    case "Cambia stipendio":
                        Console.WriteLine("Inserisci nuovo stipendio");
                        lavoratore.Stipendio = Convert.ToDecimal(Console.ReadLine());

                        break;

                    case "Cambia punteggio performance":
                        Console.WriteLine("Inserisci nuovo punteggio performance");
                        lavoratore.Performance = Convert.ToInt32(Console.ReadLine());

                        break;

                    case "Cambia giorni di assenze":
                        Console.WriteLine("Modifica giorni di assenze");
                        lavoratore.Assenze = Convert.ToInt32(Console.ReadLine());

                        break;

                    case "Cambia mail":
                        Console.WriteLine("Inserisci il nuovo indirizzo email aziendale");
                        lavoratore.Mail = Console.ReadLine().Trim();


                        break;

                    case "Esci":
                        Console.WriteLine("\nL'applicazione si sta per chiudere\n");

                        break;

                    default:
                        Console.WriteLine("\nScelta errata.Prego scegliere tra le opzioni disponibili 1-8\n");
                        break;
                }

                // se nome,cognome vengono modificati cambia anche il nome del json corrispondente

                string newFilePath = Path.Combine(directoryPath, $"{lavoratore.Nome}_{lavoratore.Cognome}.json");

                // Serializza i dati aggiornati del dipendente 
                string jsonString = JsonConvert.SerializeObject(lavoratore, Formatting.Indented);

                //Cancella il vecchio json

                File.Delete(filePath);

                //scrive il nuovo file json con i dati aggiornati serializzati

                File.WriteAllText(newFilePath, jsonString);


                Console.WriteLine("Dipendente aggiornato con successo.");
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore non trattato: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }

    // metodo per rimuovere il dipendente e il relativo file json inserendo nome,cognome nella console
    static void RimuoviDipendente()
    {

    GetNomeCognome(out string nome, out string cognome);
        string filePath = Path.Combine(directoryPath, $"{nome}_{cognome}.json");

        try
        {

            if (File.Exists(filePath))
            {
                File.Delete(filePath);    // rimuove file json
                Console.WriteLine("Dipendente rimosso con successo.");
            }
            else
            {
                Console.WriteLine("Dipendente non trovato");
            }
        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore durante la rimozione del dipendente: {e.Message}");
            Console.WriteLine($"CODICE ERRORE: {e.HResult}");
        }
    }


    //metodo per ordinare gli stipendi dal più alto al più basso e vedere alcuni  dati del dipendente

    static void SortStipendio()
    {
        var dipendenti = GetDipendenti();

        // algoritmo bubblesort modificato per ordinare il dato dello stipendio in ordine discendente 
        for (int i = 0; i < dipendenti.Count - 1; i++)
        {
            for (int j = 0; j < dipendenti.Count - i - 1; j++)
            {
                if (dipendenti[j].Stipendio < dipendenti[j + 1].Stipendio)
                {
                    var temp = dipendenti[j];
                    dipendenti[j] = dipendenti[j + 1];
                    dipendenti[j + 1] = temp;
                }


            }
        }


        var table = CreaColonne(new string[]{"Dipendente","Stipendio","Performance"});


        Console.WriteLine("\nDipendenti ordinati per stipendio in ordine discendente:\n");

        foreach (var dipendente in dipendenti)
        {
            table.AddRow($"{dipendente.Nome} {dipendente.Cognome}", $"{dipendente.Stipendio}", $"{dipendente.Performance}");

        }

        AnsiConsole.Write(table);
    }

   
    // metodo che calcola il tasso di assenteismo su un totale di 250 giorni lavorativi l'anno
    static void TassoDiAssenteismo()
    {
        Console.WriteLine("\nDi seguito l'elenco con il tasso di assenteismo per ogni dipendente su 250 giorni lavorativi equivalente ad 1 anno\n");
        int giorniLavorativiTotali = 250;

        try
        {
            var dipendenti = GetDipendenti();


            // tabella 

            var table = CreaColonne(new string[]{"Dipendente","Tasso di assenteismo"});


            // reverse- modificato la funzione sort in modo da  ordinare i dipendenti dal tasso di assenteismo più alto al più basso

            dipendenti.Sort((y, x) => x.Assenze.CompareTo(y.Assenze));

            foreach (var dipendente in dipendenti)

            {
                int assenze = dipendente.Assenze;


                double assenteismo = ((double)assenze / giorniLavorativiTotali) * 100;     // calcolo del tasso di assenteismo
                double tassoAssenteismo = Math.Round(assenteismo, 2);

                table.AddRow($"{dipendente.Nome} {dipendente.Cognome}", $"{tassoAssenteismo}%");


            }

            AnsiConsole.Write(table);

            // Tasso di assenteismo = [(giorni di assenza non giustificate) / (giorni totali di lavoro)] x 100.


        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore generale: {e.Message}");
        }

    }

    //metodo che  legge il file json e lo deserializza
    static dynamic LeggiJson(string filePath)
    {

        string jsonRead = File.ReadAllText(filePath);
        return JsonConvert.DeserializeObject<dynamic>(jsonRead);
    }

    // metodo per ordinare i dipendenti in base alle performance dividendoli in 2 gruppi in base al punteggio 
    static void ValutazionePerformance()
    {
       var dipendenti =GetDipendenti();

        Console.WriteLine("\nDivide i dipendendenti in 2 gruppi in base al rendimento");

        // ordina dipendenti per performance

        for (int i = 0; i < dipendenti.Count - 1; i++)
        {
            for (int j = 0; j < dipendenti.Count - i - 1; j++)
            {
                if (dipendenti[j].Performance < dipendenti[j + 1].Performance)
                {
                    var temp = dipendenti[j];
                    dipendenti[j] = dipendenti[j + 1];
                    dipendenti[j + 1] = temp;
                }

            }

        }

        // divide i dipendenti in 2 gruppi.Nel primo vengono inseriti quelli con le performance migliori

        int split = dipendenti.Count / 2;
        List<dynamic> squadra1 = dipendenti.GetRange(0, split);
        List<dynamic> squadra2 = dipendenti.GetRange(split, dipendenti.Count - split);

        // aggiunto tabella dipendenti con performance migliori


       var table =  CreaColonne(new string[]{"Dipendente","Performance"});

        // aggiunto tabella dipendenti con performance inferiori

        var table2 =  CreaColonne(new string[]{"Dipendente","Performance"});

        // aggiunto tabella dipendenti con performance inferiori gli ultimi 15%


        var table3 = CreaColonne(new string[]{"Dipendente","Performance"});


        // aggiunge nella tabella i dati del dipendente mettendo in evidenza le performance
        // in squadra1 vengono messi i migliori

        foreach (var impiegato in squadra1)
        {
            table.AddRow($"{impiegato.Nome} {impiegato.Cognome}", $"{impiegato.Performance}");

        }

        foreach (var impiegato in squadra2)
        {
            table2.AddRow($"{impiegato.Nome} {impiegato.Cognome}", $"{impiegato.Performance}");


        }

        Console.WriteLine("\nGruppo con le performance più alte:\n");

        AnsiConsole.Write(table);
        Console.WriteLine("\nGruppo con le performance più basse:\n");
        AnsiConsole.Write(table2);

        // ordina i valori

        squadra2.Sort((x, y) => x.Performance.CompareTo(y.Performance));

        // formula per trovare il 15% dei risultati più bassi

        int index = (15 * squadra2.Count) / 100;

        // Se il 15% è 0.5 o più, arrotonda per eccesso a 1
        if (index == 0 && squadra2.Count > 0)
        {
            index = 1;
        }

        // stampa il 15% dei risultati peggiori

        for (int i = 0; i < index; i++)
        {
            var membro = squadra2[i];
            table3.AddRow($"{membro.Nome} {membro.Cognome}", $"Performance: {membro.Performance}\n");
        }

        Console.WriteLine("\nDi seguito il 15% delle performance peggiori\n");
        AnsiConsole.Write(table3);

    }

    // funzione che calcola l'incidenza percentuale dello stipendio in rapporto al fatturato
    static void IncidenzaPercentuale()
    {
        string fileTxt = "fatturato.txt";

        double fatturato;

        if (!File.Exists(fileTxt))
        {
            Console.WriteLine("Inserisci fatturato");
            fatturato = Convert.ToDouble(Console.ReadLine());
            File.WriteAllText(fileTxt, fatturato.ToString());


        }
        else
        {
            string[] lines = File.ReadAllLines(fileTxt);
            if (lines.Length == 0)
            {
                // Se il file è vuoto o il contenuto non è valido, chiede il fatturato all'utente
                Console.WriteLine("Inserisci fatturato");
                //converte fatturato in decimale
                fatturato = Convert.ToDouble(Console.ReadLine());
                //scrive valori sul file txt convertendolo in stringa
                File.WriteAllText(fileTxt, fatturato.ToString());
            }
            else
            {
                fatturato = Convert.ToDouble(lines[0]);     // converte in double per i calcoli
            }
        }


        var dipendenti = GetDipendenti();

           // creazione tabella 

        var table =CreaColonne(new string[]{"Nome","Cognome","Data di nascita","Mansione","Stipendio","Incidenza stipendio lordo sul fatturato","Performance","Giorni di assenze"});

        dipendenti.Sort((y, x) => x.Stipendio.CompareTo(y.Stipendio));

        foreach (var dipendente in dipendenti)

        {
            double stipendio = Convert.ToDouble(dipendente.Stipendio);

            //formula Incidenza percentuale : (Cifra Inferiore / Cifra Superiore) X 100

            double costoPersonale = (stipendio / fatturato) * 100;     // calcolo del tasso d'incidenza
            double costoPercentuale = Math.Round(costoPersonale, 2);   // limite 2 cifre decimali

            //Console.WriteLine($"{dipendente.Nome} {dipendente.Cognome} {dipendente.Stipendio} {costoPercentuale}% {dipendente.Performance}");
            table.AddRow($"{dipendente.Nome}", $"{dipendente.Cognome}", $"{dipendente.DataDiNascita}", $"{dipendente.Mansione}", $"{dipendente.Stipendio}", $"{costoPercentuale}%", $"{dipendente.Performance}", $"{dipendente.Assenze}");

        }
        AnsiConsole.Write(table);
    }

// metodo che consente di aggiungere alla lista dinamica i dipendenti dei file json
    static List<dynamic> GetDipendenti()
{
    // prende in considerazione tutti i file di estensione .json

    var files = Directory.GetFiles(directoryPath, "*.json");
     // creazione di una lista di tipo dynamic permette poi di manipolare gli oggetti deserializzati da JSON 
    List<dynamic> dipendenti = new List<dynamic>();
      //cicla dentro la directory dipendenti scorrendo tutti i file e aggiungendo i dipendenti alla lista

    foreach (var file in files)
    {
        var dipendente = LeggiJson(file);
        dipendenti.Add(dipendente);
    }

    return dipendenti;
}
    // metodo per creare la tabella con spectre console in modo da visualizzare tutti i dati del dipendente
    static dynamic CreaTabella(string filePath)
    {
         var dipendente = LeggiJson(filePath);

        var table = CreaColonne(new string[]{"Nome","Cognome","Data di nascita","Mansione","Stipendio annuale","Performance","Giorni di assenza","Email aziendale"});

        table.AddRow($"{dipendente.Nome}", $"{dipendente.Cognome}", $"{dipendente.DataDiNascita}", $"{dipendente.Mansione}", $"{dipendente.Stipendio}", $"{dipendente.Performance}", $"{dipendente.Assenze}", $"{dipendente.Mail}");

        return table;
    }

// metodo per creare le colonne delle tabelle con Spectre console
    static Table CreaColonne(string[]colonne){
        var table = new Table().Border(TableBorder.Square);

        foreach(string colonna in colonne){
            table.AddColumn(new TableColumn(colonna).Centered());

        }
        return table;
    }
//metodo per inserire l'input da console nome,cognome
    static void GetNomeCognome(out string nome, out string cognome)
{
    while (true)
    {
        Console.WriteLine("\nInserisci nome e cognome del dipendente separati da virgola");
        var inserisciNome = Console.ReadLine();
        var nomi = inserisciNome.Split(',');

        if (nomi.Length == 2)
        {
            nome = nomi[0].Trim();
            cognome = nomi[1].Trim();
            return;
        }
        else
        {
            Console.WriteLine("L'input deve contenere esattamente due valori separati da virgola: nome e cognome.");
        }
    }
}


}

```

</details>

# IMPLEMENTAZIONE 7 VERSIONE FINALE CORREZIONE FILE DOPPI

- Implementato timestamp nell'oggetto per tenere traccia dell'orario di creazione di ogni json 
- Concatenato nome del file json con timestamp per distinguere i file con lo stesso nome e cognome
- Modificato la logica di ricerca,modifica,rimozione dei file json con implementazione di un menu per distinguere i file doppi e   scegliere su quale file operare


<details>
    <summary>Visualizza il codice</summary>


```csharp

using Newtonsoft.Json;
using Spectre.Console;

class Program
{

    // crea cartella dipendenti dove verranno messi i file json per ogni dipendente
    static string directoryPath = @"dipendenti/";
    static void Main(string[] args)

    {
        // se la cartella non esiste la crea

        if (!Directory.Exists(directoryPath))
        {
            Directory.CreateDirectory(directoryPath);
        }

        Console.WriteLine("Benvenuto nel programma di gestione del personale.");

        // variabile per il menu di spectre console
        var opzione = "";

        do
        {
            Console.Clear();

            // creazione del menu con spectre console
            opzione = AnsiConsole.Prompt(
         new SelectionPrompt<string>()
        .Title("GESTIONALE PERSONALE")
        .PageSize(9)
        .MoreChoicesText("[grey](Move up and down to reveal more)[/]")
        .AddChoices(new[] {
            "Inserisci dipendente","Visualizza dipendenti","Cerca dipendente",
            "Modifica dipendente","Rimuovi dipendente","Tasso di assenteismo","Valutazione performance","Ordina stipendi","Rapporto stipendio fatturato","Esci",
        }));

            // scelta del tipo di azione da svolgere

            switch (opzione)
            {
                case "Inserisci dipendente":
                    InserisciDipendente();
                    break;
                case "Visualizza dipendenti":
                    VisualizzaDipendenti();
                    break;
                case "Cerca dipendente":
                    CercaDipendente();
                    break;
                case "Modifica dipendente":
                    ModificaDipendente();
                    break;
                case "Rimuovi dipendente":
                    RimuoviDipendente();
                    break;
                case "Tasso di assenteismo":
                    TassoDiAssenteismo();
                    break;
                case "Valutazione performance":

                    ValutazionePerformance();
                    break;
                case "Ordina stipendi":

                    SortStipendio();
                    break;
                case "Rapporto stipendio fatturato":

                    IncidenzaPercentuale();
                    break;
                case "Esci":
                    Console.WriteLine("Il programma verrà chiuso. Attendere prego.");
                    break;
                default:
                    Console.WriteLine("Errore di scelta: Prego riprovare");
                    break;
            }

            // se viene scelta l'opzione 9 il programma si chiude altrimenti prosegue

            if (opzione != "Esci")
            {
                Console.WriteLine("\nPremere un tasto per proseguire");
                Console.ReadKey();
            }

        } while (opzione != "Esci");
    }

    // funzione per inserire i dati del dipendente e creare il relativo json

    static void InserisciDipendente()
    {
        do
        {
            try
            {

                Console.WriteLine("Inserisci nome, cognome, data di nascita DD/MM/YYYY,mansione, stipendio,voto performance da 1 a 100 ,giorni di assenze,email,separate da virgola\n");

                // accetta l'input dei dati da console
                string? inserimento = Console.ReadLine();

                // permette l'inserimento di più valori divisi dalla virgola

                string[] dati = inserimento.Split(',');

                if (dati.Length != 8)
                {
                    throw new FormatException("L'input deve contenere esattamente otto valori separati da virgola");
                }

                // formattazione data di nascita
                //ParseExact permette di specificare esattamente come vogliamo il formato  della data converte da stringa a oggetto Datetime

                DateTime dataDiNascita = DateTime.ParseExact(dati[2].Trim(), "dd/MM/yyyy", null);

                //viene riconvertito in stringa
                string dataDiNascitaFormatted = dataDiNascita.ToString("dd/MM/yyyy");

                //  creazione di un oggetto dipendente contenente i dati richiesti dall'applicazione
                var dipendente = new
                {
                    Nome = dati[0].Trim(),
                    Cognome = dati[1].Trim(),
                    DataDiNascita = dataDiNascitaFormatted, //DateTime.Parse(dati[2].Trim()),
                    Mansione = dati[3].Trim(),
                    Stipendio = Convert.ToDecimal(dati[4].Trim()),
                    Performance = Convert.ToInt32(dati[5].Trim()),
                    Assenze = Convert.ToInt32(dati[6].Trim()),
                    Mail = dati[7].Trim(),
                    TimeStamp = DateTime.Now.ToString("yyyy-MM-dd_HH-mm-ss")
                };

                // serializza l'oggetto in una stringa Json e lo indenta per renderlo più leggibile

                string jsonString = JsonConvert.SerializeObject(dipendente, Formatting.Indented);

                // Path.Combine concatena il path della cartella dipendenti al path dei file json di ogni dipendente
                string filePath = Path.Combine(directoryPath, $"{dipendente.Nome}_{dipendente.Cognome}_{dipendente.TimeStamp}.json");

                //scrive il file

                File.WriteAllText(filePath, jsonString);
            }

            catch (Exception e)
            {
                Console.WriteLine($"ERRORE INSERIMENTO DATI: {e.Message}");     // messaggio eccezione
                Console.WriteLine($"CODICE ERRORE:{e.HResult}");                //codice numerico eccezione
                return;
            }


            // se si svuole terminare l'immissione della registrazione del dipendente basta digitare n

            Console.WriteLine("Vuoi inserire un altro dipendente? (s/n)");
            string? risposta = Console.ReadLine().Trim().ToLower();

            if (risposta == "n")
            {
                break;
            }
        } while (true);


    }
    // funzione per visualizzare tutti i dipendenti con le relative caratteristiche
    static void VisualizzaDipendenti()
    {
        // analizza tutti i file con estensione .json dentro la directoryPath(cartella dipendenti)
        var files = Directory.GetFiles(directoryPath, "*.json");  //

        // verifica se c'è almeno un file per eseguire il codice
        if (files.Length > 0)
        {
            Console.WriteLine("Lista dipendenti completa con tutti i dati:\n");

            // creazione tabella dipendenti
      

            var table = CreaColonne(new string[]{"Nome","Cognome","Data di nascita","Mansione","Stipendio annuale","Performance","Giorni di assenza","Email aziendale"});


            // aggiunge nella tabella i dati di tutti i dipendenti presi dai json

            foreach (var file in files)
            {


                var dipendente = LeggiJson(file);


                table.AddRow($"{dipendente.Nome}", $"{dipendente.Cognome}", $"{dipendente.DataDiNascita}", $"{dipendente.Mansione}", $"{dipendente.Stipendio}", $"{dipendente.Performance}", $"{dipendente.Assenze}", $"{dipendente.Mail}");


            }
            var final = files.AsEnumerable().OrderBy(x => x[0]);
            AnsiConsole.Write(table);
        }
        else
        {
            Console.WriteLine("Nessun dipendente nel database.");
        }
    }

    // metodo per cercare il dipendente inserendo nome,cognome
    static void CercaDipendente()
{
    try
    {
        Console.Clear();
        // cerca i file JSON corrispondenti al nome e cognome forniti dall'utente e ne ritorna il path 
          string filePath = RicercaJson(out string nome, out string cognome);

        if (filePath != null)
        {
            var table = CreaTabella(filePath);
            AnsiConsole.Write(table);
        }
    }
    catch (Exception e)
    {
        Console.WriteLine($"Errore non trattato: {e.Message}");
        Console.WriteLine($"CODICE ERRORE: {e.HResult}");
    }
}
    
    //cerca dipendente per nome,cognome e poi modifica le caratteristiche del dipendente a scelta

   static void ModificaDipendente()
{
    try
    {
        string filePath = RicercaJson(out string nome, out string cognome);

        if (filePath != null)
        {
            var lavoratore = LeggiJson(filePath);
            var inserimento = AnsiConsole.Prompt(
                new SelectionPrompt<string>()
                .Title("MODIFICA DIPENDENTE")
                .PageSize(8)
                .MoreChoicesText("[grey](Move up and down to reveal more)[/]")
                .AddChoices(new[] {
                    "Cambia nome","Cambia cognome","Cambia data di nascita formato DD/MM/YYYY",
                    "Cambia mansione","Cambia stipendio","Cambia punteggio performance","Cambia giorni di assenze","Cambia mail","Esci",
                }));

            switch (inserimento)
            {
                case "Cambia nome":
                    Console.WriteLine("Inserici il nuovo nome");
                    lavoratore.Nome = Console.ReadLine().Trim();
                    break;
                case "Cambia cognome":
                    Console.WriteLine("Inserici il nuovo cognome");
                    lavoratore.Cognome = Console.ReadLine().Trim();
                    break;
                case "Cambia data di nascita formato DD/MM/YYYY":
                    Console.WriteLine("Inserisci nuova data di nascita");
                    lavoratore.DataDiNascita = DateTime.ParseExact(Console.ReadLine().Trim(), "dd/MM/yyyy", null).ToString("dd/MM/yyyy");
                    break;
                case "Cambia mansione":
                    Console.WriteLine("Inserisci nuova mansione");
                    lavoratore.Mansione = Console.ReadLine().Trim();
                    break;
                case "Cambia stipendio":
                    Console.WriteLine("Inserisci nuovo stipendio");
                    lavoratore.Stipendio = Convert.ToDecimal(Console.ReadLine());
                    break;
                case "Cambia punteggio performance":
                    Console.WriteLine("Inserisci nuovo punteggio performance");
                    lavoratore.Performance = Convert.ToInt32(Console.ReadLine());
                    break;
                case "Cambia giorni di assenze":
                    Console.WriteLine("Modifica giorni di assenze");
                    lavoratore.Assenze = Convert.ToInt32(Console.ReadLine());
                    break;
                case "Cambia mail":
                    Console.WriteLine("Inserisci il nuovo indirizzo email aziendale");
                    lavoratore.Mail = Console.ReadLine().Trim();
                    break;
                case "Esci":
                    Console.WriteLine("\nL'applicazione si sta per chiudere\n");
                    return;
                default:
                    Console.WriteLine("\nScelta errata. Prego scegliere tra le opzioni disponibili 1-8\n");
                    return;
            }

            string newFilePath = Path.Combine(directoryPath, $"{lavoratore.Nome}_{lavoratore.Cognome}_{DateTime.Now:yyyy-MM-dd_HH-mm-ss}.json");
            string jsonString = JsonConvert.SerializeObject(lavoratore, Formatting.Indented);

            File.Delete(filePath);
            File.WriteAllText(newFilePath, jsonString);

            Console.WriteLine("Dipendente aggiornato con successo.");
        }
    }
    catch (Exception e)
    {
        Console.WriteLine($"Errore non trattato: {e.Message}");
        Console.WriteLine($"CODICE ERRORE: {e.HResult}");
    }
}


    // metodo per rimuovere il dipendente e il relativo file json inserendo nome,cognome nella console
static void RimuoviDipendente()
{
    try
    {
        string filePath = RicercaJson(out string nome, out string cognome);

        if (filePath != null)
        {
            File.Delete(filePath);
            Console.WriteLine("Dipendente rimosso con successo.");
        }
    }
    catch (Exception e)
    {
        Console.WriteLine($"Errore durante la rimozione del dipendente: {e.Message}");
        Console.WriteLine($"CODICE ERRORE: {e.HResult}");
    }
}


    //metodo per ordinare gli stipendi dal più alto al più basso e vedere alcuni  dati del dipendente

    static void SortStipendio()
    {
        var dipendenti = GetDipendenti();

        // algoritmo bubblesort modificato per ordinare il dato dello stipendio in ordine discendente 
        for (int i = 0; i < dipendenti.Count - 1; i++)
        {
            for (int j = 0; j < dipendenti.Count - i - 1; j++)
            {
                if (dipendenti[j].Stipendio < dipendenti[j + 1].Stipendio)
                {
                    var temp = dipendenti[j];
                    dipendenti[j] = dipendenti[j + 1];
                    dipendenti[j + 1] = temp;
                }


            }
        }

        var table = CreaColonne(new string[]{"Dipendente","Stipendio","Performance"});

        Console.WriteLine("\nDipendenti ordinati per stipendio in ordine discendente:\n");

        foreach (var dipendente in dipendenti)
        {
            table.AddRow($"{dipendente.Nome} {dipendente.Cognome}", $"{dipendente.Stipendio}", $"{dipendente.Performance}");

        }

        AnsiConsole.Write(table);
    }

   
    // metodo che calcola il tasso di assenteismo su un totale di 250 giorni lavorativi l'anno
    static void TassoDiAssenteismo()
    {
        Console.WriteLine("\nDi seguito l'elenco con il tasso di assenteismo per ogni dipendente su 250 giorni lavorativi equivalente ad 1 anno\n");
        int giorniLavorativiTotali = 250;

        try
        {
            var dipendenti = GetDipendenti();


            // tabella 

            var table = CreaColonne(new string[]{"Dipendente","Tasso di assenteismo"});


            // reverse- modificato la funzione sort in modo da  ordinare i dipendenti dal tasso di assenteismo più alto al più basso

            dipendenti.Sort((y, x) => x.Assenze.CompareTo(y.Assenze));

            foreach (var dipendente in dipendenti)

            {
                int assenze = dipendente.Assenze;


                double assenteismo = ((double)assenze / giorniLavorativiTotali) * 100;     // calcolo del tasso di assenteismo
                double tassoAssenteismo = Math.Round(assenteismo, 2);

                table.AddRow($"{dipendente.Nome} {dipendente.Cognome}", $"{tassoAssenteismo}%");


            }

            AnsiConsole.Write(table);

            // Tasso di assenteismo = [(giorni di assenza non giustificate) / (giorni totali di lavoro)] x 100.


        }
        catch (Exception e)
        {
            Console.WriteLine($"Errore generale: {e.Message}");
        }

    }

    //metodo che  legge il file json e lo deserializza
    static dynamic LeggiJson(string filePath)
    {

        string jsonRead = File.ReadAllText(filePath);
        return JsonConvert.DeserializeObject<dynamic>(jsonRead);
    }

    // metodo per ordinare i dipendenti in base alle performance dividendoli in 2 gruppi in base al punteggio 
    static void ValutazionePerformance()
    {
       var dipendenti =GetDipendenti();

        Console.WriteLine("\nDivide i dipendendenti in 2 gruppi in base al rendimento");

        // ordina dipendenti per performance

        for (int i = 0; i < dipendenti.Count - 1; i++)
        {
            for (int j = 0; j < dipendenti.Count - i - 1; j++)
            {
                if (dipendenti[j].Performance < dipendenti[j + 1].Performance)
                {
                    var temp = dipendenti[j];
                    dipendenti[j] = dipendenti[j + 1];
                    dipendenti[j + 1] = temp;
                }

            }

        }

        // divide i dipendenti in 2 gruppi.Nel primo vengono inseriti quelli con le performance migliori

        int split = dipendenti.Count / 2;
        List<dynamic> squadra1 = dipendenti.GetRange(0, split);
        List<dynamic> squadra2 = dipendenti.GetRange(split, dipendenti.Count - split);

        // aggiunto tabella dipendenti con performance migliori


       var table =  CreaColonne(new string[]{"Dipendente","Performance"});

        // aggiunto tabella dipendenti con performance inferiori

        var table2 =  CreaColonne(new string[]{"Dipendente","Performance"});

        // aggiunto tabella dipendenti con performance inferiori gli ultimi 15%


        var table3 = CreaColonne(new string[]{"Dipendente","Performance"});


        // aggiunge nella tabella i dati del dipendente mettendo in evidenza le performance
        // in squadra1 vengono messi i migliori

        foreach (var impiegato in squadra1)
        {
            table.AddRow($"{impiegato.Nome} {impiegato.Cognome}", $"{impiegato.Performance}");

        }

        foreach (var impiegato in squadra2)
        {
            table2.AddRow($"{impiegato.Nome} {impiegato.Cognome}", $"{impiegato.Performance}");


        }

        Console.WriteLine("\nGruppo con le performance più alte:\n");

        AnsiConsole.Write(table);
        Console.WriteLine("\nGruppo con le performance più basse:\n");
        AnsiConsole.Write(table2);

        // ordina i valori

        squadra2.Sort((x, y) => x.Performance.CompareTo(y.Performance));

        // formula per trovare il 15% dei risultati più bassi

        int index = (15 * squadra2.Count) / 100;

        // Se il 15% è 0.5 o più, arrotonda per eccesso a 1
        if (index == 0 && squadra2.Count > 0)
        {
            index = 1;
        }

        // stampa il 15% dei risultati peggiori

        for (int i = 0; i < index; i++)
        {
            var membro = squadra2[i];
            table3.AddRow($"{membro.Nome} {membro.Cognome}", $"Performance: {membro.Performance}\n");
        }

        Console.WriteLine("\nDi seguito il 15% delle performance peggiori\n");
        AnsiConsole.Write(table3);

    }

    // funzione che calcola l'incidenza percentuale dello stipendio in rapporto al fatturato
    static void IncidenzaPercentuale()
    {
        string fileTxt = "fatturato.txt";

        double fatturato;

        if (!File.Exists(fileTxt))
        {
            Console.WriteLine("Inserisci fatturato");
            fatturato = Convert.ToDouble(Console.ReadLine());
            File.WriteAllText(fileTxt, fatturato.ToString());


        }
        else
        {
            string[] lines = File.ReadAllLines(fileTxt);
            if (lines.Length == 0)
            {
                // Se il file è vuoto o il contenuto non è valido, chiede il fatturato all'utente
                Console.WriteLine("Inserisci fatturato");
                //converte fatturato in decimale
                fatturato = Convert.ToDouble(Console.ReadLine());
                //scrive valori sul file txt convertendolo in stringa
                File.WriteAllText(fileTxt, fatturato.ToString());
            }
            else
            {
                fatturato = Convert.ToDouble(lines[0]);     // converte in double per i calcoli
            }
        }


        var dipendenti = GetDipendenti();

           // creazione tabella 

        var table =CreaColonne(new string[]{"Nome","Cognome","Data di nascita","Mansione","Stipendio","Incidenza stipendio lordo sul fatturato","Performance","Giorni di assenze"});

        dipendenti.Sort((y, x) => x.Stipendio.CompareTo(y.Stipendio));

        foreach (var dipendente in dipendenti)

        {
            double stipendio = Convert.ToDouble(dipendente.Stipendio);

            //formula Incidenza percentuale : (Cifra Inferiore / Cifra Superiore) X 100

            double costoPersonale = (stipendio / fatturato) * 100;     // calcolo del tasso d'incidenza
            double costoPercentuale = Math.Round(costoPersonale, 2);   // limite 2 cifre decimali

            //Console.WriteLine($"{dipendente.Nome} {dipendente.Cognome} {dipendente.Stipendio} {costoPercentuale}% {dipendente.Performance}");
            table.AddRow($"{dipendente.Nome}", $"{dipendente.Cognome}", $"{dipendente.DataDiNascita}", $"{dipendente.Mansione}", $"{dipendente.Stipendio}", $"{costoPercentuale}%", $"{dipendente.Performance}", $"{dipendente.Assenze}");

        }
        AnsiConsole.Write(table);
    }



// metodo che consente di aggiungere alla lista dinamica i dipendenti dei file json
    static List<dynamic> GetDipendenti()
{
    // prende in considerazione tutti i file di estensione .json

    var files = Directory.GetFiles(directoryPath, "*.json");
     // creazione di una lista di tipo dynamic permette poi di manipolare gli oggetti deserializzati da JSON 
    List<dynamic> dipendenti = new List<dynamic>();
      //cicla dentro la directory dipendenti scorrendo tutti i file e aggiungendo i dipendenti alla lista

    foreach (var file in files)
    {
        var dipendente = LeggiJson(file);
        dipendenti.Add(dipendente);
    }

    return dipendenti;
}
    // metodo per creare la tabella con spectre console in modo da visualizzare tutti i dati del dipendente
    static dynamic CreaTabella(string filePath)
    {
         var dipendente = LeggiJson(filePath);

        var table = CreaColonne(new string[]{"Nome","Cognome","Data di nascita","Mansione","Stipendio annuale","Performance","Giorni di assenza","Email aziendale"});

        table.AddRow($"{dipendente.Nome}", $"{dipendente.Cognome}", $"{dipendente.DataDiNascita}", $"{dipendente.Mansione}", $"{dipendente.Stipendio}", $"{dipendente.Performance}", $"{dipendente.Assenze}", $"{dipendente.Mail}");

        return table;
    }

// metodo per creare le colonne delle tabelle con Spectre console
    static Table CreaColonne(string[]colonne){
        var table = new Table().Border(TableBorder.Square);

        foreach(string colonna in colonne){
            table.AddColumn(new TableColumn(colonna).Centered());

        }
        return table;
    }



static string RicercaJson(out string nome, out string cognome)
{
    // Prompt nome cognome
    GetNomeCognome(out nome, out cognome);

    // pattern di ricerca per il file json
    string searchPattern = $"{nome}_{cognome}_*.json";

    // prende files corrispondenti dalla directory
    var matchingFiles = Directory.GetFiles(directoryPath, searchPattern);

    // Controlla corrispondenza pattern del file
    if (matchingFiles.Length == 0)
    {
        Console.WriteLine("Dipendente non trovato");
        return null;
    }

    // Select(Path.GetFileName) estrae i nomi di ogni file json dal path e poi li converte in una lista per poi usarli nel menu
    var fileNames = matchingFiles.Select(Path.GetFileName).ToList();

    // Menu di scelta del file per l'utente
    var selectedFile = AnsiConsole.Prompt(
        new SelectionPrompt<string>()
        .Title("Seleziona il file del dipendente:")
        .PageSize(10)
        .AddChoices(fileNames)); // contiene i nomi dei file json trovati nella directory che corrispondono al pattern di ricerca.

    // Ritorna path completo del file scelto.Questo percorso può poi essere utilizzato dal programma per leggere, modificare o cancellare il file.
    return Path.Combine(directoryPath, selectedFile);
}


//metodo per inserire l'input da console nome,cognome
    static void GetNomeCognome(out string nome, out string cognome)
{
    // while utilizzato per ripetere la richiesta di input fino a quando l'utente inserisce dati validi.

    while (true)
    {
        Console.WriteLine("\nInserisci nome e cognome del dipendente separati da virgola");
        var inserisciNome = Console.ReadLine();
        var nomi = inserisciNome.Split(',');

        if (nomi.Length == 2)
        {
            nome = nomi[0].Trim();
            cognome = nomi[1].Trim();
            return;
        }
        else
        {
            Console.WriteLine("L'input deve contenere esattamente due valori separati da virgola: nome e cognome.");
        }
    }
}

    }

```


</details>