---
title: 'Vorgehensweise: Erstellen einer. VSCT-Datei | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6456b0b866f08956862fa197719354bedf0ecf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-vsct-file"></a>Vorgehensweise: Erstellen einer. VSCT-Datei  
  
Es gibt mehrere Möglichkeiten zum Erstellen einer XML-basierte Visual Studio Command Table-Konfigurationsdatei (VSCT).  
  
-   Sie erstellen ein neues VSPackage in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Paket-Vorlage.  
  
-   Den XML-basierten Befehl Tabelle Konfiguration Compiler Vsct.exe, können Sie um eine Datei aus einer vorhandenen CTC-Datei zu generieren.  
  
-   Vsct.exe können Sie um eine VSCT-Datei aus einer vorhandenen CTO-Datei zu generieren.  
  
-   Sie können eine neue VSCT-Datei manuell erstellen.  
  
 In diesem Thema erläutert, wie eine neue VSCT-Datei manuell zu erstellen.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>So erstellen Sie eine neue VSCT-Datei manuell  
  
1.  Starten Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Auf der **Datei** Sie im Menü **neu**, und klicken Sie dann auf **Datei**.  
  
3.  In der **Vorlagen** Bereich, klicken Sie auf **XML-Datei** , und klicken Sie dann auf **öffnen**.  
  
4.  Auf der **Ansicht** Menü klicken Sie auf **Fenster "Eigenschaften"** zum Anzeigen der Eigenschaften der XML-Datei.  
  
5.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche zum Durchsuchen (...), für die Eigenschaft des Schemas.  
  
6.  Wählen Sie in der Liste der XSD-Schemas das vsct.xsd-Schema. Wenn es sich nicht in der Liste ist, klicken Sie auf **hinzufügen** und klicken Sie dann die Datei auf einem lokalen Laufwerk. Klicken Sie auf **OK** sobald Sie fertig sind.  
  
7.  Geben Sie in der XML-Datendatei `<CommandTable` und drücken Sie dann die Registerkarte ". Schließen Sie das Tag dazu `>`.  
  
     Dadurch wird eine grundlegende VSCT-Datei erstellt.  
  
8.  Füllen Sie die Elemente der XML-Datei, die Sie hinzufügen möchten, die gemäß der [VSCT-Schema](../../extensibility/vsct-xml-schema-reference.md). Weitere Informationen finden Sie unter [Authoring. VSCT-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTC-Datei  
  
Sie können eine XML-basierte VSCT-Datei anhand einer vorhandenen CTC-Quelldatei erstellen. Auf diese Weise können Sie anhand der neuen XML-basierte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Befehlstabellen (VSCT).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTC-Datei  
  
1.  Rufen Sie eine Kopie der Sprache Perl ab.  
  
2.  Rufen Sie eine Kopie des Perl-Skripts ConvertCTCToVSCT.pl, in der Regel der  *\<Visual Studio SDK-Installationspfad >* \VisualStudioIntegration\Tools\bin Ordner.  
  
3.  Rufen Sie eine Kopie der CTC-Quelldatei ab, die Sie konvertieren möchten.  
  
4.  Speichern Sie die Dateien im selben Verzeichnis.  
  
5.  In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Eingabeaufforderungsfenster, navigieren Sie zu dem Verzeichnis.  
  
6.  Geben Sie Folgendes ein:  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     Dabei ist "PkgCmd.ctc" der Name der CTC-Datei, und "PkgCmd.vsct" ist der Name der VSCT-Datei, die Sie erstellen möchten.  
  
     Dadurch wird eine neue VSCT-XML-Quelldatei erstellt. Sie können die Datei mit "Vsct.exe", dem VSCT-Compiler, wie jede andere VSCT-Datei kompilieren.  
  
    > [!NOTE]
    >  Sie können die Lesbarkeit der VSCT-Datei verbessern, indem Sie die XML-Kommentare neu formatieren.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Gewusst wie: Erstellen einer VSCT-Datei anhand einer vorhandenen CTO-Datei  
  
Sie können eine XML-basierte VSCT-Datei anhand einer vorhandenen binären CTO-Datei erstellen. Diese Vorgehensweise ermöglicht es Ihnen, das neue Befehlstabellen-Compilerformat zu nutzen. Dies funktioniert sogar, wenn die CTO-Datei aus einer CTC-Datei kompiliert wurde. Sie können die VSCT-Datei bearbeiten und in eine andere CTO-Datei kompilieren.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTO-Datei  
  
1.  Erstellen Sie Kopien der CTO-Datei und der zugehörigen .CRSYM-Datei.  
  
2.  Platzieren Sie die Dateien in dem Verzeichnis, in dem sich der Compiler „vsct.exe“ befindet.  
  
3.  Navigieren Sie an der Visual Studio-Eingabeaufforderung zu dem Verzeichnis, das die CTO- und die CTSYM-Datei enthält.  
  
4.  Typ **vsct.exe** *Ctofilename *** CTO** * Vsctfilename***VSCT -S***Symfilename ***.crsym**.  
  
     `ctofilename` Der Name der CTO-Datei, `vsctfilename` ist der Name der Vsct-Datei, die Sie erstellen möchten, und `symfilename` ist der Name der ctsymdatei.  
  
     Bei diesem Vorgang wird eine neue VSCT-XML-Befehlstabellen-Compilerdatei erstellt. Sie können die Datei mit „vsct.exe“, dem vsct-Compiler, wie jede andere VSCT-Datei bearbeiten und kompilieren.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Einfach Hinzufügen einer VSCT-Datei zu einem Projekt bewirkt nicht kompilieren. Sie müssen im Buildprozess integriert sein.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Hinzufügen eine VSCT-Datei zu kompilieren des Projekts  
  
1.  Öffnen Sie die Projektdatei im Editor. Wenn das Projekt geladen wird, müssen Sie es zunächst entladen.  
  
2.  Hinzufügen einer [ItemGroup-Element](../../msbuild/itemgroup-element-msbuild.md) , ein VSCTCompile-Element enthält, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Das ResourceName-Element sollte immer festgelegt werden, um `Menus.ctmenu`.  
  
3.  Wenn Ihr Projekt eine RESX-Datei enthält, fügen Sie ein EmbeddedResource-Element, das ein Element MergeWithCTO enthält hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Dieses Markup sollte in der ItemGroup-Element aufgenommen, das eingebettete Ressourcen enthält.  
  
4.  Öffnen Sie die Paketdatei, die in der Regel mit dem Namen *Projektname*Package.cs oder *Projektname*Package.vb, im Editor.  
  
5.  Fügen Sie ein ProvideMenuResource-Attribut für die Paketklasse, wie im folgenden Beispiel dargestellt.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Der erste Parameterwert muss der Wert des Attributs ResourceName übereinstimmen, die Sie in der Projektdatei definiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen. VSCT-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)