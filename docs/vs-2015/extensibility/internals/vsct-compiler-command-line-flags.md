---
title: VSCT-Compiler-Befehlszeilenflags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 628c9ef34fc23776672a4252886c091a38f63b4b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734970"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT-Compiler-Befehlszeilenflags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Visual Studio Befehl Tabelle (VSCT)-Compiler bietet Befehlszeilenschalter, um sicherzustellen, dass erfolgreiche Kompilierung der VSCT-Dateien.  
  
## <a name="command-line-parameters"></a>Befehlszeilenparameter  
 Zum Anzeigen der grundlegenden VSCT-Hilfe aus einem [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Befehl** Fenster Navigieren Sie zu der *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Tools\Bin\-Ordner, und geben:  
  
```  
vsct /?  
```  
  
 Dadurch werden zurückgegeben:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indicate what additional include paths to send to the preprocessor  
  -L    Specify the language to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        followed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependency checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Die Zeichen - (Bindestrich) und / (Schrägstrich) sind beide akzeptierte Notation zum Angeben der Befehlszeilenparameter.  
  
 Zulässige Kennzeichen und ihre Bedeutung sind wie folgt.  
  
|Schalter|Beschreibung|  
|------------|-----------------|  
|-D|Geben Sie keine zusätzlichen definierten Symbole.|  
|-ICH|Geben Sie die zusätzliche Pfade enthalten, die beim Auflösen von Dateiverweisen verwendet werden soll.|  
|-L|Geben Sie die <xref:System.Globalization.CultureInfo> Kulturnamen, z. B. "En-US".|  
|-E|Ausgeben C# Objekte in den angegebenen Namespace für Elemente des Befehls, gefolgt von [C&#124;H&#124;N]:*Filename*, C = C#, H C++-Header, N = = Namespace. Der Namespace ist für C#-Code erforderlich.|  
|-v|Ausführliche Ausgabe.|  
  
 Der Schalter – L weist den Compiler an, wählen Sie eine Gruppe von Zeichenfolgen, die den binären CTO-Datei zu erstellen, das entspricht, dem angegebenen <xref:System.Globalization.CultureInfo> Kulturname. Der Name der angegebenen Kultur sollte die Language-Attribut von einem oder mehreren entsprechen [Strings-Element](../../extensibility/strings-element.md) in der VSCT-Datei. Wenn ein Zeichenfolgen-Element keine Language-Attribut aufweist, wird es aus dem entsprechenden geerbt [CommandTable-Element](../../extensibility/commandtable-element.md).  
  
 VSCT-Datei kann mehrere Zeichenfolgen-Elemente vorhanden, und jedes kann ein anderes Language-Attribut haben. Globalisierung wird erreicht, den VSCT-Compiler mehrfach ausführen, und ändern die -L-Option für die einzelnen Kulturname.  
  
 Wenn der Kulturname, der vom Schalter – L erhält nicht die Language-Attribut eines Elements Zeichenfolgen übereinstimmt, versucht der Compiler verwenden, entsprechend der Sprache und nicht die Region. Beispielsweise, wenn "En-US" nicht gefunden werden kann, versucht der Compiler "En" stattdessen verwenden. Führt, wird die aktuelle Kultur des Betriebssystems versucht. Führt, wird das erste Element der Zeichenfolgen, die, das Sie findet, statt.  
  
 Der -E-Schalter kann verwendet werden, eine Headerdatei für die C-Format ausgeben, die die Symbole enthält, die von der Befehlstabelle verwendet werden oder um eine C#-Datei auszugeben, die Objekte für die Befehls-Symbole enthält.  
  
 -D und -Switches haben Sie die Syntax die Cl.exe C-Präprozessor-Flags, die den gleichen Namen haben. – D Definitionen, die das Format X = Y auf werden verwendet, für die Erweiterung des XML-basierte \<definierte > tests in `Condition` Attribute. – Ich Standardincludepfade werden zum Auflösen von \<Include >, \<"extern" > und \<Bitmap > Dateiverweise. Weitere Informationen finden Sie unter den [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
 Der VSCT-Compiler kann auch eine bereits erstellte binäre Datei dekompilieren. Zu diesem Zweck geben Sie eine Binärdatei für die \<Eingabedatei >.   Wenn die Binärdatei vom dem VSCT-Compiler erstellt wurde, müssen die Symbole, die bereits eingebettet und erzeugt die Ausgabe mit der die symbolischen Namen in einem \<Symbole > Teil der Ausgabe. Wenn Binärdateien von der CTC-Compiler erstellt wurde, sind für die Ausgabe enthält die tatsächliche GUIDs und IDs. Wenn die *.ctsym-Datei, die vom aktuellen Versionen von Ctc.exe erzeugt wird im gleichen Ordner wie die Binärdatei für die Eingabe ist, die Symbole aus dieser Datei geladen und für die Ausgabe verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)   
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

