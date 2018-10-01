---
title: 'Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTC-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 0d267e6046539001cbe454ab69867c02f0a606ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521228"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTC-Datei
Sie können eine XML-basierte VSCT-Datei anhand einer vorhandenen CTC-Quelldatei erstellen. Auf diese Weise profitieren Sie von der neuen XML-basierte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Befehlstabellen (VSCT).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTC-Datei  
  
1.  Rufen Sie eine Kopie der Sprache Perl ab.  
  
2.  Rufen Sie eine Kopie des Perl-Skripts "convertctctovsct.pl" ab, in der Regel im Verzeichnis der  *\<Visual Studio SDK-Installationspfad >* \VisualStudioIntegration\Tools\bin-Ordner.  
  
3.  Rufen Sie eine Kopie der CTC-Quelldatei ab, die Sie konvertieren möchten.  
  
4.  Speichern Sie die Dateien im selben Verzeichnis.  
  
5.  In der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im Administrator-Eingabeaufforderungsfenster, navigieren Sie zu dem Verzeichnis.  
  
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