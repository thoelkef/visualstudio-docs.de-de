---
title: "Dialogfeld &quot;Erweiterte Buildeinstellungen&quot; (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.AdvancedBuildSettings"
helpviewer_keywords: 
  - "Buildoptionen [C#], erweitert"
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Dialogfeld &quot;Erweiterte Buildeinstellungen&quot; (C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie das Dialogfeld **Erweiterte Buildeinstellungen** des **Projekt\-Designers**, um erweiterte Eigenschaften für die Buildkonfiguration des Projekts anzugeben.  Dieses Dialogfeld ist nur für [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]\-Projekte relevant.  
  
## Allgemein  
 Mithilfe der folgenden Optionen können Sie allgemeine erweiterte Einstellungen festlegen.  
  
 **Sprachversion**  
 Gibt an, welche Sprachversion verwendet werden soll.  Der Umfang der Features ist in jeder Version unterschiedlich. Daher können Sie mithilfe dieser Option den Compiler anweisen, nur eine Teilmenge der implementierten Features zuzulassen oder nur die Features zu aktivieren, die mit einem vorhandenen Standard kompatibel sind.  Diese Einstellung weist die folgenden Optionen auf:  
  
-   **ISO\-1**  
  
     Legt die ISO\-1\-Standardfeatures zugrunde.  
  
-   **default**  
  
     Legt die aktuelle Version zugrunde.  
  
 Weitere Informationen finden Sie unter [\/langversion \(Conformant Syntax\)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).  
  
 **Bericht für internen Compilerfehler**  
 Gibt an, ob Compilerfehler an Microsoft weitergeleitet werden.  Bei Festlegung auf **prompt** \(Standardeinstellung\) wird beim Auftreten eines internen Compilerfehlers eine Eingabeaufforderung angezeigt. Sie können dann entscheiden, ob ein Fehlerbericht elektronisch an Microsoft gesendet werden soll.  Bei Festlegung auf **send** wird automatisch ein Fehlerbericht gesendet.  Bei Festlegung auf **queue**werden die Fehlerberichte in eine Warteschlange gestellt.  Wird die Option hingegen auf **none** festgelegt, wird der Fehler nur in der Textausgabe des Compilers gemeldet.  Weitere Informationen finden Sie unter [\/errorreport \(Set Error Reporting Behavior\)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).  
  
 **Auf arithmetischen Über\-\/Unterlauf überprüfen**  
 Gibt an, ob eine Ganzzahlarithmetikanweisung, die sich nicht im Gültigkeitsbereich des [checked](/dotnet/csharp/language-reference/keywords/checked)\-Schlüsselworts bzw. des [unchecked](/dotnet/csharp/language-reference/keywords/unchecked)\-Schlüsselworts befindet und einen Wert außerhalb des Datentypbereichs generiert, eine Laufzeitausnahme auslöst. Weitere Informationen finden Sie unter [\/checked \(Check Integer Arithmetic\)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).  
  
 **Nicht auf mscorlib.dll verweisen**  
 Gibt an, ob mscorlib.dll zur Definition des gesamten <xref:System>\-Namespaces in das Programm importiert wird.  Aktivieren Sie dieses Feld, wenn Sie einen eigenen <xref:System>\-Namespace und eigene Objekte definieren oder erstellen möchten.  Weitere Informationen finden Sie unter [\/nostdlib \(Do Not Import Standard Library\)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).  
  
## Output  
 Mit den folgenden Optionen können Sie erweiterte Ausgabeoptionen festlegen.  
  
 **Debuginformationen**  
 Gibt die Art der vom Compiler generierten Debuginformationen an.  Weitere Informationen zum Konfigurieren der Debugleistung einer Anwendung finden Sie unter [Erleichtern des Debuggens für ein Abbild](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md).  Diese Einstellung weist die folgenden Optionen auf:  
  
-   **Keine**  
  
     Gibt an, dass keine Debuginformationen generiert werden.  
  
-   **full**  
  
     Ermöglicht das Anfügen eines Debuggers an das ausgeführte Programm.  
  
-   **pdbonly**  
  
     Ermöglicht das Debuggen von Quellcode, wenn das Programm im Debugger gestartet wird. Der Assembler wird jedoch nur angezeigt, wenn das laufende Programm an den Debugger angefügt ist.  
  
 Weitere Informationen finden Sie unter [\/debug \(Emit Debugging Information\)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).  
  
 **Dateianordnung**  
 Gibt die Größe der Abschnitte in der Ausgabedatei an.  Gültige Werte sind **512**, **1024**, **2048**, **4096** und **8192**.  Diese Werte werden in Bytes angegeben.  Jeder Abschnitt wird an einer Grenze ausgerichtet, die einem Vielfachen dieses Werts entspricht. Dies wirkt sich auf die Größe der Ausgabedatei aus.  Weitere Informationen finden Sie unter [\/filealign \(Specify Section Alignment\)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).  
  
 **DLL\-Basisadresse**  
 Gibt die bevorzugte Basisadresse zum Laden einer DLL\-Datei an.  Die Standardbasisadresse für eine DLL wird von der Common Language Runtime von [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] festgelegt.  Weitere Informationen finden Sie unter [\/baseaddress \(Specify Base Address of DLL\)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).  
  
## Siehe auch  
 [C\# Compiler Options](/dotnet/csharp/language-reference/compiler-options/index)   
 [Seite "Erstellen", Projekt\-Designer \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md)