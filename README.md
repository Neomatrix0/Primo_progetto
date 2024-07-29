
 # PROGETTAZIONE APPLICAZIONE GESTIONE  RISORSE UMANE

## GESTIONE PERSONALE   

Questa applicazione console permetterà la gestione del personale in un azienda,valutando performance,stipendi,mansioni,ore di lavoro e tasso di assenteismo.
Verranno divisi i dipendenti in 2 gruppi in base al punteggio di produttività e verranno segnalati il 15 % dei dipendenti meno performanti.
Mostra i dati relativi a stipendi e  assenze del personale calcolando in percentuale il tasso di assenteismo di ognuno.

## DEFINIZIONE DEI REQUISITI E ANALISI

L'applicazione consente ad una azienda di monitorare il personale,valutarne le performance e i costi

- [ ] L'applicazione consente di inserire il nome e cognome della persona assunta,età,mansione,score di produttività da 0 a 100,stipendio,tasso di assenteismo,mail aziendale

- [ ] Visualizzazione dei dipendenti inseriti con i relativi dati anagrafici 

- [ ] Possibilità di  cercare il singolo dipendente inserendo nome,cognome



## PIANIFICAZIONE E DESIGN DELL'ARCHITETTURA

- [ ] Impostazione del menu generale con opzioni di scelta

- [ ] Opzione di inserimento del personale con dati inseriti in modo intervallato da virgola(Split),dettagli anagrafici,stipendio,mansione,contratto,performance,assenze e salvataggio dati nel file json

- [ ] Opzione di visualizzazione di tutto il personale con i relativi dati

- [ ]  Opzione di ricerca del singolo dipendente inserendo nome,cognome

- [ ]  Modifica dati dipendente e implementazione di un sottomenu per scegliere il singolo campo da modificare


#  PRIMA VERSIONE DEL CODICE SEMPLIFICATA

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

# COMANDI VERSIONAMENTO

```bash

git status
git add --all
git commit -m "first-commit"
git push -u origin main

```

# IMPLEMENTAZIONI VERSIONE 2

- Aggiungere funzioni modifica,creando sottomenu dove scegliere l'opzione da modificare
- Modifica del menu principale aggiungendo nuovi case per accogliere le nuove funzioni
- Aggiunta della funzione RimuoviDipendente() per rimuovere il singolo dipendente dal programma e il relativo file json

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

- Aggiunta funzione TassoDiAssenteismo()
- Aggiunta funzione ValutazionePerformance()
- Aggiunta funzione SortStipendio()

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


# IMPLEMENTAZIONI VERSIONE 4 FINALE SENZA SPECTRE CONSOLE   

- Implementazioni funzione GetFile()
- Implementazione funzione IncidenzaPercentuale()
- Implementazione funzione ReadJson() 
- Pulizia e refactoring del codice utilizzando le nuove funzioni menzionate per eliminare ridondanze

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


