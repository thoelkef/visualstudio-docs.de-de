# <a name="metadata-and-markdown-template"></a>Metadaten und Markdownvorlage

Diese core-docs-Vorlage enthält Beispiele der Markdownsyntax sowie einen Leitfaden zum Festlegen der Metadaten. Um die Vorlage bestmöglich zu nutzen, müssen Sie sowohl das [unformatierte Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) als auch die [gerenderte Ansicht](https://github.com/dotnet/docs/blob/master/styleguide/template.md) anzeigen (beispielsweise zeigt das unformatierte Markdown, anders als die gerenderte Ansicht, den Metadatenblock an).

Beim Erstellen einer Markdowndatei sollten Sie diese Vorlage in eine neue Datei kopieren, die Metadaten wie nachstehend angegeben ausfüllen, den H1-Header oben als Titel des Artikels festlegen und den Inhalt löschen. 


## <a name="metadata"></a>Metadaten 

Der vollständige Metadatenblock befindet sich oben (im [unformatierten Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)), unterteilt in erforderliche Felder und optionale Felder. Wichtige Hinweise:

- Bei einem Metadatenelement **muss** ein Leerzeichen zwischen dem Doppelpunkt (:) und dem Wert stehen.
- Wenn ein optionales Metadatenelement über keinen Wert verfügt, kommentieren Sie das Element mit einem # aus, oder entfernen Sie es (lassen Sie es nicht leer, und verwenden Sie nicht „n/v“). Wenn Sie einem Element, das auskommentiert wurde, einen Wert hinzufügen, denken Sie daran, das # zu entfernen.
- Doppelpunkte in einem Wert (z.B. einem Titel) unterbrechen den Metadatenparser. In diesem Fall setzen Sie den Titel in doppelte Anführungszeichen (z.B. `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).
- 
  **title**: Dieser Titel wird in Suchergebnissen angezeigt. Sie können auch einen senkrechten Strich (|), gefolgt vom Produktnamen, hinzufügen (z.B. `title: Developing Libraries with Cross Platform Tools | .NET Core`). Der Titel muss nicht mit dem Titel in Ihrem H1-Header übereinstimmen, und er sollte höchstens 65 Zeichen (inklusive | PRODUKTNAME) umfassen.
- **author**, **manager**, **ms.reviewer**: Das Feld „author“ sollte den **GitHub-Benutzernamen** des Autors enthalten, nicht dessen Alias.  Andererseits sollten die Felder „manager“ und „ms.reviewer“ Microsoft-Aliase enthalten. „ms.reviewer“ gibt den Namen des PM/dev an, der dem Artikel oder der Funktion zugeordnet ist.
- **ms.devlang** definiert die Technologie. Einige der unterstützten Werte sind: dotnet, cpp, csharp, fsharp, vb und xml.
- **ms.assetid**: Dies ist die GUID des Artikels, die für interne Zwecke wie z.B. Business Intelligence (BI) verwendet wird. Wenn Sie eine neue Markdowndatei erstellen, rufen Sie eine GUID von [https://www.guidgenerator.com](https://www.guidgenerator.com) ab. 

## <a name="basic-markdown-gfm-and-special-characters"></a>Grundlegendes Markdown, GFM und Sonderzeichen

Alles grundlegende Markdown sowie GitHub Flavored Markdown (GFM) wird unterstützt. Weitere Informationen dazu finden Sie auf den folgenden Seiten:

- [Grundlegende Markdownsyntax](https://daringfireball.net/projects/markdown/syntax)
- [GFM-Dokumentation](https://guides.github.com/features/mastering-markdown)

Markdown verwendet Sonderzeichen wie z.B. \*, \`, und \# für die Formatierung. Wenn Sie eines dieser Zeichen in Ihren Inhalt einschließen möchten, müssen Sie einen der folgenden Schritte ausführen:

- Setzen Sie einen umgekehrten Schrägstrich vor das Sonderzeichen, um es mit einem Escapezeichen zu versehen (z.B. `\*` für \*)
- Verwenden Sie den [HTML-Entitätscode](http://www.ascii.cl/htmlcodes.htm) für das Zeichen (z.B. `&#42;` für ein &#42;).

## <a name="file-name"></a>Dateiname

Dateinamen verwenden die folgenden Regeln:
* Es sollten nur Kleinbuchstaben, Zahlen und Bindestriche enthalten sein.
* Keine Leer- oder Interpunktionszeichen. Verwenden Sie die Bindestriche zum Trennen von Wörtern und Zahlen im Dateinamen.
* Verwenden Sie genaue Aktionsverben wie „entwickeln“, „kaufen“, „erstellen“ oder „beheben“. Keine englischen Wörter mit der Endung „-ing“
* Keine kurzen Wörter – verwenden Sie nicht „ein/eine/einer“, „und“, „der/die/das“, „in“, „oder“ usw.
* Muss in Markdown geschrieben werden und die Dateierweiterung .md verwenden.
* Halten Sie Dateinamen einigermaßen kurz. Sie sind Teil der URL für Ihre Artikel.  



## <a name="headings"></a>Kopfzeilen

Verwenden Sie die übliche Groß-/Kleinschreibung. Folgendes sollte immer groß geschrieben werden:
- Das erste Wort eines Headers 
- Das erste Wort nach einem Doppelpunkt in einem Titel oder einer Überschrift (z.B. „Vorgehensweise: Sortieren eines Arrays“). 

Überschriften sollten mithilfe des atx-Stils erstellt werden, d.h. es sollten 1-6 Hash-Zeichen (#) am Anfang der Zeile verwendet werden, um eine Überschrift anzugeben, entsprechend der HTML-Überschriftenebenen H1 bis H6. Beispiele für Header der ersten und zweiten Ebene werden oben verwendet. 

In Ihrem Thema **darf** nur eine Überschrift der ersten Ebene (H1) enthalten sein, die als Titel auf der Seite angezeigt wird.

Wenn Ihre Überschrift mit dem Zeichen `#` endet, müssen Sie ein zusätzliches `#`-Zeichen am Ende einfügen, damit der Titel richtig gerendert wird. Beispielsweise `# Async Programming in F# #`.     

Überschriften der zweiten Ebene generieren das Inhaltsverzeichnis auf der Seite, das im Abschnitt „In diesem Artikel“ unterhalb des Titels auf der Seite angezeigt wird.

### <a name="third-level-heading"></a>Überschrift der dritten Ebene
#### <a name="fourth-level-heading"></a>Überschrift der vierten Ebene
##### <a name="fifth-level-heading"></a>Überschrift der fünften Ebene
###### <a name="sixth-level-heading"></a>Überschrift der sechsten Ebene
 
## <a name="text-styling"></a>Textstil

*Kursiv*: wird für Dateien, Ordner, Pfade (lange Pfade sollten in einer eigenen Zeile stehen), neue Begriffe und URLs (sofern diese nicht entsprechend dem Standard als Links gerendert werden) verwendet.

**Fett** wird für Benutzeroberflächenelemente verwendet.

## <a name="links"></a>Links

### <a name="internal-links"></a>Interne Links

Um auf einen Header in der gleichen Markdowndatei zu verlinken (auch als Ankerlinks bekannt), müssen Sie die ID des Headers ermitteln, auf den Sie verlinken möchten. Um die ID zu bestätigen, zeigen Sie die Quelle des gerenderten Artikels an, suchen Sie nach der ID des Headers (z.B. `id="blockquote"`), und erstellen Sie den Link mithilfe von # + ID (z.B. `#blockquote`).
Die ID wird basierend auf dem Headertext automatisch generiert. Wenn also beispielsweise ein eindeutiger Abschnitt `## Step 2` genannt wird, sieht die ID folgendermaßen aus: `id="step-2"`.

- Beispiel: [Kapitel 1](#chapter-1)

Um auf eine Markdowndatei im gleichen Repository zu verlinken, verwenden Sie [relative Links](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), einschließlich „.md“ am Ende des Dateinamens.

- Beispiel: [Infodatei](../readme.md)
- Beispiel: [Welcome to .NET (Willkommen bei .NET)](../docs/welcome.md)

Um auf einen Header in einer Markdowndatei im gleichen Repository zu verlinken, verwenden Sie die relative Verlinkung + die Hashtag-Verlinkung.

- Beispiel: [.NET Community (.NET-Community)](../docs/welcome.md#community)

### <a name="external-links"></a>Externe Links

Um auf eine externe Datei zu verlinken, verwenden Sie als Link die vollständige URL.

- Beispiel: [GitHub](http://www.github.com)

Wenn in einer Markdowndatei eine URL erscheint, wird diese in einen klickbaren Link verwandelt.

- Ein Beispiel: http://www.github.com

### <a name="links-to-apis"></a>Links zu APIs

Das Buildsystem verfügt über einige Erweiterungen, die es ermöglichen, auf .NET Core-APIs zu verlinken, ohne externe Links verwenden zu müssen.  
Wenn auf eine API verlinkt wird, können Sie deren eindeutigen Bezeichner (UID) verwenden, der automatisch aus dem Quellcode generiert wird.

Sie können eine der folgenden Syntaxen verwenden:
1. Markdownlink: `[link_text](xref:UID)`
2. Automatischer Link: `<xref:UID>`
3. Kurzform: `@UID`

- Ein Beispiel: `@System.String`
- Ein Beispiel: `[String class](xref:System.String)` 

Weitere Informationen zur Verwendung dieser Notation finden Sie unter [Using cross reference (Verwenden von Querverweisen)](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference).

> Im Moment gibt es keine einfache Möglichkeit, nach den UIDs zu suchen. Die beste Möglichkeit, nach der UID für eine API zu suchen, ist, im folgenden Repository zu suchen: [docascode/coreapi](https://github.com/docascode/coreapi). Wir arbeiten daran, in Zukunft über ein besseres System zu verfügen.

Wenn die UID die Sonderzeichen \` und \# enthält, muss der UID-Wert als %60 und %23 entsprechend HTML-codiert werden, wie in den folgenden Beispielen:
- Beispiel: @System.Threading.Tasks.Task\`1 wird zu `@System.Threading.Tasks.Task%601`
- Beispiel: @System.Exception\#ctor wird zu `@System.Exception.%23ctor`

## <a name="lists"></a>Listen

### <a name="ordered-lists"></a>Geordnete Liste

1. Dies 
1. Ist
1. Eine
1. Geordnete
1. Liste  


#### <a name="ordered-list-with-an-embedded-list"></a>Geordnete Liste mit einer eingebetteten Liste

1. Hier
1. kommt
1. eine
1. eingebettete
    1. Fräulein Gloria
    1. Professor Bloom
1. geordnete
1. Liste


### <a name="unordered-lists"></a>Ungeordnete Listen

- Dies
- ist
- eine
- Aufzählungs-
- Liste


##### <a name="unordered-list-with-an-embedded-list"></a>Ungeordnete Liste mit einer eingebetteten Liste

- Diese 
- Aufzählungs- 
- Liste
    - Baronin von Porz
    - Reverend Grün
- enthält  
- andere
    1. Oberst von Gatow
    1. Frau Weiß
- Listen


## <a name="horizontal-rule"></a>Horizontale Regel

---

## <a name="tables"></a>Tabellen

| Tabellen        | Sind           | Toll  |
| ------------- |:-------------:| -----:|
| col 3 ist      | rechtsbündig | $1600 |
| col 2 ist      | zentriert      |   $12 |
| col 1 ist der Standard | linksbündig     |    $1 |

Sie können ein [Markdowntool zum Generieren von Tabellen](http://www.tablesgenerator.com/markdown_tables) verwenden, um diese einfacher zu erstellen. 

## <a name="code"></a>Code

Die beste Methode zum Einschließen von Code ist, Codeausschnitte aus einem funktionierenden Beispiel einzuschließen. Erstellen Sie Ihr Beispiel, indem Sie die Anweisungen im [Leitfaden für Mitwirkende](../CONTRIBUTING.md#contributing-to-samples) befolgen.

Sie können den Code mithilfe von einschließender Syntax einschließen:

```
[!code-csharp[<title>](<pathToFile>#<RegionName)]
```

Das obige Beispiel zeigt die C#-Syntax, andere Sprachen werden jedoch unterstützt.
Verwenden Sie `code-fsharp` für F#-Beispiele; verwenden Sie `code-vbnet` für Visual Basic-Beispiele.
Andere unterstützte Sprachen sind:
* C++: `code-cpp`
* HTML: `code-html`
* JavaScript: `code-javascript`
* PowerShell: `code-ps`
* SQL: `code-sql`
* XML: `code-xml`



Der Text, den Sie für `<title>` festlegen, wird als Rollover auf dem Text angezeigt. `<pathToFile>` ist der Pfad zur Quelldatei. `<RegionName>` sollte ein Bereich in Ihrem Quellcode sein, der eingeschlossen werden sollte. Verwenden Sie die Präprozessorsyntax `#region` und `#endregion`, um den Codebereich anzugeben, der eingeschlossen werden soll.

Bei Fällen, in denen Bereiche nicht funktionieren, können Sie den Beginn und das Ende eines Ausschnitts angeben, indem Sie einen XML-Elementnamen in einem einzeiligen Kommentar verwenden. Beispielsweise könnten Sie Folgendes in C# schreiben:

```csharp
// <CodeToInclude>
int j = 5;
int i ; 10;
int sum = i + j;
// </CodeToInclude>
```

In anderen Sprachen verwenden Sie die Kommentarsyntax für die jeweilige Sprache.
Schließlich können Sie Zeilennummern verwenden: `#L1-L10` würde die Zeilen 1-10 einschließen. Wir raten von Zeilennummern ab, da diese sehr anfällig sind.

Durch das Einschließen von Ausschnitten aus vollen Programmen wird sichergestellt, dass der gesamte Code durch unser Continuous Integration-System (CI) läuft. Wenn Sie jedoch etwas zeigen müssen, das Kompilierzeit- oder Laufzeitfehler verursacht, können Sie Inlinecodeblöcke verwenden.

### <a name="inline-code-blocks-with-language-identifier"></a>Inlinecodeblöcke mit Sprachen-ID

Verwenden Sie drei Graviszeichen (\`\`\`) + eine Sprachen-ID, um die sprachenspezifische Farbcodierung für einen Codeblock anzuwenden. Hier finden Sie die gesamte Liste der [GFM-Sprachen-IDs](https://github.com/jmm/gfm-lang-ids/wiki/GitHub-Flavored-Markdown-(GFM)-language-IDs).

##### <a name="c9839"></a>C&#9839;

```c#
using System;
namespace HelloWorld
{
    class Hello 
    {
        static void Main() 
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```
#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```
#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>Generischer Codeblock

Verwenden Sie drei Graviszeichen (&#96;&#96;&#96;) für die Codierung mit generischem Codeblock.   

> Die empfohlene Vorgehensweise ist, Codeblöcke mit Sprachen-IDs wie im vorherigen Abschnitt beschrieben zu verwenden, um sicherzustellen, dass auf der Dokumentationsseite die richtige Syntax hervorgehoben wird. Verwenden Sie generische Codeblöcke nur bei Bedarf.

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

### <a name="inline-code"></a>Inlinecode

Verwenden Sie Graviszeichen (&#96;) für `inline code`. Verwenden Sie Inlinecode für Befehlszeilenbefehle, Datenbanktabellennamen und -spaltennamen sowie Sprachschlüsselwörter.

## <a name="blockquotes"></a>Blockquotes

> Die Dürre hatte schon zehn Millionen Jahre angehalten, und die Herrschaft der Schrecklichen Saurier war lange vorbei. Hier am Äquator, auf dem Kontinent, der eines Tages Afrika heißen würde, hatte der Existenzkampf ein neues Stadium von Grausamkeit erreicht und ein Gewinner war noch nicht abzusehen. In diesem ausgetrockneten, ausgedörrten Land konnte nur der Kleinste oder der Schnellste oder der Zäheste gedeihen oder zu überleben hoffen.

## <a name="images"></a>Bilder

### <a name="static-image-or-animated-gif"></a>Statisches Bild oder animiertes GIF

![Dies ist der Alternativtext](../images/Logo_DotNet.png)

### <a name="linked-image"></a>Verlinktes Bild

[![Alternativtext für verlinktes Bild](../images/Logo_DotNet.png)](https://dot.net) 

## <a name="videos"></a>Videos

### <a name="channel-9"></a>Channel 9

<iframe src="https://channel9.msdn.com/Shows/On-NET/Shipping-NET-Core-RC2--Tools-Preview-1/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/g2a4W6Q7aRw" frameborder="0" allowfullscreen></iframe>

## <a name="docsmicrosoft-extensions"></a>docs.microsoft-Erweiterungen

docs.microsoft bietet einige zusätzliche Erweiterungen zu GitHub Flavored Markdown. 

### <a name="alerts"></a>Benachrichtigungen

Es ist wichtig, die folgenden Warnstile zu verwenden, damit diese im richtigen Stil auf der Dokumentationsseite gerendert werden. Die Rendering-Engine auf GitHub unterscheidet diese jedoch nicht.     

#### <a name="note"></a>Hinweis

> [!NOTE]
> Dies ist ein HINWEIS

#### <a name="warning"></a>Warnung

> [!WARNING]
> Dies ist eine WARNUNG

#### <a name="tip"></a>Tipp

> [!TIP]
> Dies ist ein TIPP

#### <a name="important"></a>Wichtig

> [!IMPORTANT]
> Dies ist WICHTIG

Und sie werden wie folgt gerendert: ![Warnstile](../images/alerts.png)

### <a name="buttons"></a>Schaltflächen

> [!div class="button"]
[Schaltflächenlinks](../docs/core/index.md)

Ein Beispiel für Schaltflächen in Aktion finden Sie in der [Intune-Dokumentation](https://docs.microsoft.com/en-us/intune/get-started/choose-how-to-enroll-devices). 

### <a name="selectors"></a>Selektoren

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Windows](../docs/core/tutorials/using-on-windows.md)

Ein Beispiel für Selektoren in Aktion finden Sie in der [Intune-Dokumentation](https://docs.microsoft.com/en-us/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune#how-your-end-users-get-their-apps).

### <a name="step-by-steps"></a>Schritt-für-Schritt-Funktionen

>[!div class="step-by-step"]
[Zurück](../docs/csharp/expression-trees-interpreting.md)
[Weiter](../docs/csharp/expression-trees-translating.md)

Ein Beispiel für Schritt-für-Schritt-Funktionen in Aktion finden Sie in der [Dokumentation für Advanced Threat Analytics](https://docs.microsoft.com/en-us/advanced-threat-analytics/deploy-use/install-ata-step2).