---
title: "Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTC-Datei | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT-Dateien, anhand einer CTC-Datei erstellen"
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTC-Datei
Sie können eine XML\-basierte VSCT\-Datei anhand einer vorhandenen CTC\-Quelldatei erstellen. Dabei können Sie das neue XML\-basierte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Command Table\-Compilerformat \(VSCT\) nutzen.  
  
### So erstellen Sie eine VSCT\-Datei anhand einer CTC\-Datei  
  
1.  Rufen Sie eine Kopie der Sprache Perl ab.  
  
2.  Rufen Sie eine Kopie des Perl\-Skripts "ConvertCTCToVSCT.pl" ab, das sich normalerweise im Ordner "*\<Visual Studio SDK\-Installationspfad\>*\\VisualStudioIntegration\\Tools\\bin" befindet.  
  
3.  Rufen Sie eine Kopie der CTC\-Quelldatei ab, die Sie konvertieren möchten.  
  
4.  Speichern Sie die Dateien im selben Verzeichnis.  
  
5.  Navigieren Sie im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Eingabeaufforderungsfenster zu dem Verzeichnis.  
  
6.  Geben Sie Folgendes ein:  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     Dabei ist "PkgCmd.ctc" der Name der CTC\-Datei, und "PkgCmd.vsct" ist der Name der VSCT\-Datei, die Sie erstellen möchten.  
  
     Dadurch wird eine neue VSCT\-XML\-Quelldatei erstellt. Sie können die Datei mit "Vsct.exe", dem VSCT\-Compiler, wie jede andere VSCT\-Datei kompilieren.  
  
    > [!NOTE]
    >  Sie können die Lesbarkeit der VSCT\-Datei verbessern, indem Sie die XML\-Kommentare neu formatieren.  
  
## Siehe auch  
 [Gewusst wie: Erstellen einer. VSCT\-Datei](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)