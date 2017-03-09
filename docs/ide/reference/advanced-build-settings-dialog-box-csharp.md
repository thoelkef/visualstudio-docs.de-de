---
title: "Dialogfeld „Erweiterte Buildeinstellungen“ (C#) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 82ec5d2db35da72beb017e15d1c271f751b5f56b
ms.lasthandoff: 02/22/2017

---
# <a name="advanced-build-settings-dialog-box-c"></a>Dialogfeld "Erweiterte Buildeinstellungen" (C#)
Verwenden Sie das Dialogfeld **Erweiterte Buildeinstellungen** des **Projekt-Designers**, um die erweiterten Buildkonfigurationseigenschaften des Projekts anzugeben. Dieses Dialogfeld gilt nur für [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]-Projekte.  
  
## <a name="general"></a>Allgemein  
 Die folgenden Optionen geben Ihnen die Möglichkeit, allgemeine erweiterte Einstellungen vorzunehmen.  
  
 **Sprachversion**  
 Gibt die Version der zu verwendenden Sprache an. Die Funktionsgruppe ist für jede Version anders, weshalb diese Option dazu verwendet werden kann, den Compiler dazu zu zwingen, nur eine Untergruppe von implementierten Funktionen zu erlauben oder nur die Funktionen zu aktivieren, die mit einem bereits vorhandenen Standard kompatibel sind. Diese Einstellung hat folgende Optionen:  
  
-   **ISO-1**  
  
     Setzt die ISO-1 Standardfunktionen als Ziel.  
  
-   **default**  
  
     Setzt die aktuellen Version als Ziel.  
  
 Weitere Informationen finden Sie unter [/langversion (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).  
  
 **Bericht für interne Compilerfehler**  
 Gibt an, ob Compilerfehler an Microsoft gemeldet werden sollen. Wenn **prompt** (Standardeinstellung) eingestellt ist, erhalten Sie eine Aufforderung, wenn ein interner Compilerfehler auftritt, die Ihnen die Option gibt, einen elektronischen Fehlerbericht an Microsoft zu senden. Wenn **send** eingestellt ist, werden Fehlerberichte automatisch gesendet. Wenn **queue** eingestellt ist, werden Fehlerberichte in eine Warteschlange gestellt. Wenn **none** eingestellt ist, wird der Fehler nur in der Eingabe des Compilertexts gemeldet. Weitere Informationen finden Sie unter [/errorreport (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).  
  
 **Auf arithmetischen Über-/Unterlauf überprüfen**  
 Gibt an, ob ein arithmetischer Ganzzahlauszug, der sich außerhalb des Bereichs der [geprüften](/dotnet/csharp/language-reference/keywords/checked) oder [ungeprüften](/dotnet/csharp/language-reference/keywords/unchecked) Schlüsselwörter befindet und der einen Wert außerhalb des Bereichs des Datentyps nach sich zieht, eine Ausnahme verursacht. Weitere Informationen finden Sie unter [/checked (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).  
  
 **Nicht auf mscorlib.dll verweisen**  
 Gibt an, ob mscorlib.dll in Ihr Programm importiert wird und damit den gesamten Namespace <xref:System> definiert. Aktivieren Sie dieses Kästchen , wenn Sie Ihren eigenen Namespace <xref:System> und die entsprechenden Objekte definieren oder erstellen möchten. Weitere Informationen finden Sie unter [/nostdlib (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).  
  
## <a name="output"></a>Ausgabe  
 Die folgenden Optionen geben Ihnen die Möglichkeit, erweiterte Ausgabeoptionen anzugeben.  
  
 **Informationen zum Debuggen**  
 Gibt den Typ der Debuginformationen an, die vom Compiler generiert werden. Informationen zur Konfiguration der Leistung einer Anwendung beim Debuggen finden Sie unter [Erleichtern des Debuggens für ein Image](http://msdn.microsoft.com/Library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Diese Einstellung hat folgende Optionen:  
  
-   **none**  
  
     Gibt an, das keine Informationen zum Debuggen generiert werden  
  
-   **full**  
  
     Ermöglicht es, einen Debugger an ein ausgeführtes Programm anzufügen.  
  
-   **pdbonly**  
  
     Macht ein Debuggen von Quellcode möglich, wenn das Programm im Debugger gestartet wird. Der Assembler wird jedoch nur angezeigt, wenn das aktive Programm an den Debugger angefügt ist.  
  
 Weitere Informationen finden Sie unter [/debug (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).  
  
 **Dateianordnung**  
 Gibt die Größe der Abschnitte in der Ausgabedatei an. Gültige Werte sind **512**, **1024**, **2048**, **4096** und **8192**. Diese Werte werden in Bytes angegeben. Jeder Abschnitt wird auf einer Grenze angeordnet, die ein Mehrfaches des Werts ist, wodurch die Größe der Ausgabedatei beeinflusst wird. Weitere Informationen finden Sie unter [/filealign (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).  
  
 **DLL-Basisadresse**  
 Gibt die bevorzugte Basisadresse an, unter der eine DLL geladen werden soll. Die Standard-Basisadresse für eine DLL-Datei wird durch die [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]-Common Language Runtime festgelegt. Weitere Informationen finden Sie unter [/baseaddress (C# Compiler Options)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Compileroptionen](/dotnet/csharp/language-reference/compiler-options/index)   
 [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md)
