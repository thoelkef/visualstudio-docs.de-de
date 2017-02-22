---
title: "VSCT-Compiler-Befehlszeilen-Flags | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT-Dateien, kompilieren"
  - "Datei Befehlstabelle Kompilierung (VSCT-Dateien)"
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# VSCT-Compiler-Befehlszeilen-Flags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Visual Studio Befehl Tabelle (VSCT)-Compiler bietet Befehlszeilenschalter, um sicherzustellen, dass erfolgreichen Kompilierung VSCT-Dateien.  
  
## <a name="command-line-parameters"></a>Befehlszeilenparameter  
 Zum Anzeigen der grundlegenden VSCT-Hilfe aus eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Befehl** Fenster, navigieren Sie zu der *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Tools\Bin\-Ordner, und geben:  
  
```  
vsct /?  
```  
  
 Dadurch werden zurückgegeben:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Die Zeichen - (Bindestrich) und / (Schrägstrich) sind beide akzeptierte Notation für Befehlszeilenparameter angibt.  
  
 Zulässige Kennzeichen und ihre Bedeutung sind wie folgt.  
  
|Schalter|Beschreibung|  
|------------|-----------------|  
|-D|Geben Sie zusätzliche definierten Symbole.|  
|-I:|Geben Sie die zusätzliche Pfade enthalten, die beim Auflösen von Dateiverweisen verwendet werden soll.|  
|-L|Geben Sie die <xref:System.Globalization.CultureInfo> Kulturnamen, z. B. "En-US".|  
|– E|Ausgeben von C#-Objekte im angegebenen Namespace für Befehl Elemente, gefolgt von [C &#124; H &#124; N]:*Filename*in dem C = C#-, H = C++-Header, N = Namespace. Der Namespace ist für c# erforderlich.|  
|-v|Eine ausführliche Ausgabe.|  
  
 Der -L-Switch weist den Compiler, wählen Sie eine Gruppe von Zeichenfolgen, die den binären CTO-Datei erzeugen, das entspricht, dem angegebenen <xref:System.Globalization.CultureInfo> Kulturname. Der angegebene Kulturname übereinstimmen, die Language-Attribut aus einem oder mehreren [Zeichenfolgen Element](../../extensibility/strings-element.md) in der VSCT-Datei. Wenn ein Zeichenfolgen-Element kein Language-Attribut verfügt, wird Sie aus dem entsprechenden geerbt [CommandTable Element](../../extensibility/commandtable-element.md).  
  
 Eine VSCT-Datei verfügt möglicherweise über mehrere Zeichenfolgen-Elemente, und jedes kann ein anderes Language-Attribut haben. Globalisierung wird erreicht, den VSCT-Compiler mehrfach ausführen, und Ändern des -L-Switches für jeden Kulturname.  
  
 Wenn der Kulturname, der vom Switch -L erhält nicht die Language-Attribut eines beliebigen Elements Zeichenfolgen übereinstimmt, versucht der Compiler, die Sprache und nicht die Region entsprechen. Beispielsweise, wenn "En-US" nicht gefunden werden kann, versucht der Compiler "En" stattdessen. Andernfalls wird die aktuelle Kultur des Betriebssystems versucht. Andernfalls kann das erste Element der Zeichenfolgen kompiliert werden, die, das es findet.  
  
 Der Switch -E kann verwendet werden, eine Headerdatei für die C-Format ausgeben, die die Symbole enthält, die von der Befehlstabelle verwendet werden oder eine C#-Datei ausgeben, die Objekte für die Symbole Befehl enthält.  
  
 -D "und" – I Switches verwenden, die Syntax der Präprozessor Cl.exe C-Flags, die den gleichen Namen haben. – D Definitionen, die das Format X = Y aufweisen, werden verwendet, für die Erweiterung des XML-basierte \< benutzerdefinierte> testet `Condition` Attribute. – Ich Includepfaden werden zum Auflösen von \< Include>, \< "extern"> und \< Bitmap> Dateiverweise. Weitere Informationen finden Sie unter der [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md).  
  
 VSCT-Compiler kann auch eine vorher erstellte binäre Datei dekompilieren. Zu diesem Zweck geben Sie eine Binärdatei für das \< Infile>.   Wenn die Binärdatei, die von der VSCT-Compiler erstellt wurde, müssen die Symbole bereits eingebettet und erzeugt die Ausgabe mit den symbolischen Namen in einem \< Symbole> Abschnitt der Ausgabe. Wenn die Binärdatei, die von der CTC-Compiler erstellt wurde, wird die Ausgabe der tatsächlichen-GUIDs und IDs enthalten. Wenn die *.ctsym-Datei, die vom aktuellen Versionen der Ctc.exe erzeugt wird im gleichen Ordner wie die binäre Eingabedatei ist, wird die Symbole aus dieser Datei geladen und für die Ausgabe verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)   
 [Wie VSPackages Elemente der Benutzeroberfläche hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)