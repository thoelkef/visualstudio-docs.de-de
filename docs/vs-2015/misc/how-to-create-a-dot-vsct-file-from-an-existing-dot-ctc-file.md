---
title: 'Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTC-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: e159fea34dc395ce2d7bded813f2d8feaa453006
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303484"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTC-Datei
Sie können eine XML-basierte VSCT-Datei anhand einer vorhandenen CTC-Quelldatei erstellen. Dabei können Sie das neue XML-basierte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Command Table-Compilerformat (VSCT) nutzen.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTC-Datei  
  
1.  Rufen Sie eine Kopie der Sprache Perl ab.  
  
2.  Rufen Sie eine Kopie des Perl-Skripts "convertctctovsct.pl" ab, in der Regel im Verzeichnis der  *\<Visual Studio SDK-Installationspfad >* \VisualStudioIntegration\Tools\bin-Ordner.  
  
3.  Rufen Sie eine Kopie der CTC-Quelldatei ab, die Sie konvertieren möchten.  
  
4.  Speichern Sie die Dateien im selben Verzeichnis.  
  
5.  Navigieren Sie im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Eingabeaufforderungsfenster zu dem Verzeichnis.  
  
6.  Geben Sie Folgendes ein:  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     Dabei ist "PkgCmd.ctc" der Name der CTC-Datei, und "PkgCmd.vsct" ist der Name der VSCT-Datei, die Sie erstellen möchten.  
  
     Dadurch wird eine neue VSCT-XML-Quelldatei erstellt. Sie können die Datei mit "Vsct.exe", dem VSCT-Compiler, wie jede andere VSCT-Datei kompilieren.  
  
    > [!NOTE]
    >  Sie können die Lesbarkeit der VSCT-Datei verbessern, indem Sie die XML-Kommentare neu formatieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen Sie ein. VSCT-Datei](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)