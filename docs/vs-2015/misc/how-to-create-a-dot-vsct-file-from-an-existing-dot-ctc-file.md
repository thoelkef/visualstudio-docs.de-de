---
title: 'Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTC-Datei | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 7b963436e9d968dd5ba3829e97d0fd0c52e49641
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443007"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTC-Datei
Sie können eine XML-basierte VSCT-Datei anhand einer vorhandenen CTC-Quelldatei erstellen. Dabei können Sie das neue XML-basierte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Command Table-Compilerformat (VSCT) nutzen.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTC-Datei  
  
1. Rufen Sie eine Kopie der Sprache Perl ab.  
  
2. Rufen Sie eine Kopie des Perl-Skripts "convertctctovsct.pl" ab, in der Regel im Verzeichnis der  *\<Visual Studio SDK-Installationspfad >* \VisualStudioIntegration\Tools\bin-Ordner.  
  
3. Rufen Sie eine Kopie der CTC-Quelldatei ab, die Sie konvertieren möchten.  
  
4. Speichern Sie die Dateien im selben Verzeichnis.  
  
5. Navigieren Sie im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Eingabeaufforderungsfenster zu dem Verzeichnis.  
  
6. Geben Sie Folgendes ein:  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     Dabei ist "PkgCmd.ctc" der Name der CTC-Datei, und "PkgCmd.vsct" ist der Name der VSCT-Datei, die Sie erstellen möchten.  
  
     Dadurch wird eine neue VSCT-XML-Quelldatei erstellt. Sie können die Datei mit "Vsct.exe", dem VSCT-Compiler, wie jede andere VSCT-Datei kompilieren.  
  
    > [!NOTE]
    > Sie können die Lesbarkeit der VSCT-Datei verbessern, indem Sie die XML-Kommentare neu formatieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen Sie ein. VSCT-Datei](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)