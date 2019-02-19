---
title: Dialogfeld „Erweiterte Buildeinstellungen“ (C#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f4336ef93eded7ed1d56a8ee34fff0189813da17
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54763347"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Dialogfeld "Erweiterte Buildeinstellungen" (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Verwenden Sie das Dialogfeld **Erweiterte Buildeinstellungen** des **Projekt-Designers**, um die erweiterten Buildkonfigurationseigenschaften des Projekts anzugeben. Dieses Dialogfeld gilt nur für [!INCLUDE[csprcs](../../includes/csprcs-md.md)]-Projekte.  
  
## <a name="general"></a>Allgemein  
 Die folgenden Optionen geben Ihnen die Möglichkeit, allgemeine erweiterte Einstellungen vorzunehmen.  
  
 **Sprachversion**  
 Gibt die Version der zu verwendenden Sprache an. Die Funktionsgruppe ist für jede Version anders, weshalb diese Option dazu verwendet werden kann, den Compiler dazu zu zwingen, nur eine Untergruppe von implementierten Funktionen zu erlauben oder nur die Funktionen zu aktivieren, die mit einem bereits vorhandenen Standard kompatibel sind. Diese Einstellung hat folgende Optionen:  
  
- **ISO-1**  
  
   Setzt die ISO-1 Standardfunktionen als Ziel.  
  
- **default**  
  
   Setzt die aktuellen Version als Ziel.  
  
  Weitere Informationen finden Sie unter [/langversion (C# Compiler Options)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).  
  
  **Bericht für interne Compilerfehler**  
  Gibt an, ob Compilerfehler an Microsoft gemeldet werden sollen. Wenn **prompt** (Standardeinstellung) eingestellt ist, erhalten Sie eine Aufforderung, wenn ein interner Compilerfehler auftritt, die Ihnen die Option gibt, einen elektronischen Fehlerbericht an Microsoft zu senden. Wenn **send** eingestellt ist, werden Fehlerberichte automatisch gesendet. Wenn **queue** eingestellt ist, werden Fehlerberichte in eine Warteschlange gestellt. Wenn **none** eingestellt ist, wird der Fehler nur in der Eingabe des Compilertexts gemeldet. Weitere Informationen finden Sie unter [/errorreport (C# Compiler Options)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).  
  
  **Auf arithmetischen Über-/Unterlauf überprüfen**  
  Gibt an, ob ein arithmetischer Ganzzahlauszug, der sich außerhalb des Bereichs der [geprüften](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) oder [ungeprüften](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) Schlüsselwörter befindet und der einen Wert außerhalb des Bereichs des Datentyps nach sich zieht, eine Ausnahme verursacht. Weitere Informationen finden Sie unter [/checked (C# Compiler Options)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).  
  
  **Nicht auf mscorlib.dll verweisen**  
  Gibt an, ob „mscorlib.dll“ in Ihr Programm importiert wird und damit den gesamten Namespace <xref:System> definiert. Klicken Sie dieses Kästchen an, wenn Sie Ihren eigenen <xref:System>-Namespace und Objekte definieren oder erstellen möchten. Weitere Informationen finden Sie unter [/nostdlib (C# Compiler Options)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).  
  
## <a name="output"></a>Output  
 Die folgenden Optionen geben Ihnen die Möglichkeit, erweiterte Ausgabeoptionen anzugeben.  
  
 **Informationen zum Debuggen**  
 Gibt den Typ der Debuginformationen an, die vom Compiler generiert werden. Informationen zur Konfiguration der Leistung einer Anwendung beim Debuggen finden Sie unter [Erleichtern des Debuggens für ein Image](http://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Diese Einstellung hat folgende Optionen:  
  
- **none**  
  
   Gibt an, das keine Informationen zum Debuggen generiert werden  
  
- **full**  
  
   Ermöglicht es, einen Debugger an ein ausgeführtes Programm anzufügen.  
  
- **pdbonly**  
  
   Macht ein Debuggen von Quellcode möglich, wenn das Programm im Debugger gestartet wird. Der Assembler wird jedoch nur angezeigt, wenn das aktive Programm an den Debugger angefügt ist.  
  
  Weitere Informationen finden Sie unter [/debug (C# Compiler Options)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).  
  
  **Dateianordnung**  
  Gibt die Größe der Abschnitte in der Ausgabedatei an. Gültige Werte sind **512**, **1024**, **2048**, **4096** und **8192**. Diese Werte werden in Bytes angegeben. Jeder Abschnitt wird auf einer Grenze angeordnet, die ein Mehrfaches des Werts ist, wodurch die Größe der Ausgabedatei beeinflusst wird. Weitere Informationen finden Sie unter [/filealign (C# Compiler Options)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).  
  
  **DLL-Basisadresse**  
  Gibt die bevorzugte Basisadresse an, unter der eine DLL geladen werden soll. Die Standard-Basisadresse für eine DLL-Datei wird durch die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Common Language Runtime festgelegt. Weitere Informationen finden Sie unter [/baseaddress (C# Compiler Options)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Compileroptionen](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)   
 [Seite „Erstellen“, Projekt-Designer (C#)](../../ide/reference/build-page-project-designer-csharp.md)
