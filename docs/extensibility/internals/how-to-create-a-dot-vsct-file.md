---
title: 'Vorgehensweise: Erstellen Sie ein. VSCT-Datei | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8dd2e677cae2e54a8dff716aef72f1d6abc6b40
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602805"
---
# <a name="how-to-create-a-vsct-file"></a>Vorgehensweise: Erstellen einer VSCT-Datei

Es gibt mehrere Möglichkeiten, um eine Tabelle-Konfiguration in XML-basierte Visual Studio-Befehl erstellen (*VSCT*) Datei.

- Sie können in ein neues VSPackage erstellen, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Paket-Vorlage.

- Sie können den XML-basierten Befehl Table Configuration-Compiler *Vsct.exe*, zum Generieren einer Datei aus einer vorhandenen *CTC* Datei.

- Können Sie *Vsct.exe* zum Generieren einer *VSCT* Datei aus einem vorhandenen *CTO* Datei.

- Sie können manuell ein neues erstellen *VSCT* Datei.

  In diesem Artikel wird erläutert, wie zum manuellen Erstellen eines neuen *VSCT* Datei.

### <a name="to-manually-create-a-new-vsct-file"></a>So erstellen Sie eine neue VSCT-Datei manuell

1. Starten Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Auf der **Datei** Startmenü **neu**, und klicken Sie dann auf **Datei**.

3. In der **Vorlagen** Bereich, klicken Sie auf **XML-Datei** , und klicken Sie dann auf **öffnen**.

4. Auf der **Ansicht** Menü klicken Sie auf **Eigenschaften** zum Anzeigen der Eigenschaften der XML-Datei.

5. In der **Eigenschaften** Fenster, klicken Sie auf die **Durchsuchen** Schaltfläche der **Schemas** Eigenschaft.

6. Wählen Sie in der Liste der XSD-Schemas, die *vsct.xsd* Schema. Wenn es sich nicht in der Liste ist, klicken Sie auf **hinzufügen** und suchen Sie dann die Datei auf einem lokalen Laufwerk. Klicken Sie auf **OK** Wenn Sie fertig sind.

7. Geben Sie in der XML-Datei, *< CommandTable* , und drücken Sie dann die **Registerkarte**. Schließen Sie das Tag, indem Sie eingeben *>*.

    Diese Aktion erstellt eine grundlegende *VSCT* Datei.

8. Geben Sie die Elemente der XML-Datei, die Sie hinzufügen möchten, die gemäß der [VSCT XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md). Weitere Informationen finden Sie unter [VSCT-Dateien erstellen](../../extensibility/internals/authoring-dot-vsct-files.md)

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Vorgehensweise: Erstellen einer VSCT-Datei aus einer vorhandenen CTC-Datei

Sie erstellen ein XML-basiertes *VSCT* Datei aus einer vorhandenen Befehlstabelle *CTC* Quelldatei. Dabei können Sie das neue XML-basierte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Command Table-Compilerformat (VSCT) nutzen.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTC-Datei

1. Rufen Sie eine Kopie der Sprache Perl ab.

2. Rufen Sie eine Kopie des Perl-Skripts *"convertctctovsct.pl" ab*in der Regel befindet sich in der  *\<Visual Studio SDK-Installationspfad > \VisualStudioIntegration\Tools\bin* Ordner.

3. Erstellen einer Kopie der *CTC* Quelldatei, die Sie konvertieren möchten.

4. Speichern Sie die Dateien im selben Verzeichnis.

5. In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] im Administrator-Eingabeaufforderungsfenster, navigieren Sie zu dem Verzeichnis.

6. Typ

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    in denen *"pkgcmd.CTC"* ist der Name des der *CTC* Datei und *"pkgcmd.VSCT"* ist der Name des der *VSCT* -Datei, die Sie erstellen möchten.

    Diese Aktion erstellt ein neues *VSCT* XML-Quelldatei. Kompilieren Sie die Datei mit *Vsct.exe*, würden Sie die VSCT-Compiler, wie Sie alle anderen *VSCT* Datei.

   > [!NOTE]
   >  Sie können die Lesbarkeit verbessern die *VSCT* Datei, die XML-Kommentare neu formatiert wird.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Vorgehensweise: Erstellen einer VSCT-Datei aus einer vorhandenen CTO-Datei

Sie erstellen ein XML-basiertes *VSCT* -Datei aus einer vorhandenen binären *CTO* Datei. Diese Vorgehensweise ermöglicht es Ihnen, das neue Befehlstabellen-Compilerformat zu nutzen. Dieser Prozess funktioniert auch, wenn die *CTO* -Datei kompiliert wurde, aus einem *CTC* Datei. Sie bearbeiten und kompilieren Sie die *VSCT* -Datei in eine andere CTO-Datei.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTO-Datei

1.  Erstellen Sie Kopien der *CTO* -Datei und der entsprechenden *.ctsym* Datei.

2.  Platzieren Sie die Dateien in demselben Verzeichnis wie die *vsct.exe* Compiler.

3.  Der Visual Studio-Eingabeaufforderung, wechseln Sie in das Verzeichnis mit dem *CTO* und *.ctsym* Dateien.

4.  Typ

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     in denen \<Ctofilename\> ist der Name des der *CTO* Datei \<Vsctfilename\> ist der Name des der *VSCT* Datei, die Sie erstellen möchten, und \<Symfilename\> ist der Name des der *.ctsym* Datei.

     Dieser Vorgang erstellt ein neues *VSCT* XML-Befehlstabellen-Compilerdatei. Sie können auch bearbeiten und kompilieren Sie die Datei mit *vsct.exe*, würden Sie die Vsct-Compiler, wie Sie alle anderen *VSCT* Datei.

## <a name="compile-the-code"></a>Kompilieren des Codes
 Hinzufügen einer *VSCT* -Datei zu einem Projekt bewirkt nicht kompilieren. Sie müssen es im Buildprozess integrieren.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>Projekt-Kompilierung einer VSCT-Datei hinzu

1.  Öffnen Sie die Projektdatei im Editor. Wenn das Projekt geladen wird, müssen Sie es zunächst entladen.

2.  Hinzufügen einer [ItemGroup-Element](../../msbuild/itemgroup-element-msbuild.md) , enthält eine `VSCTCompile` Element, wie im folgenden Beispiel dargestellt.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     Die `ResourceName` Element sollte immer festgelegt werden, um `Menus.ctmenu`.

3.  Wenn das Projekt enthält eine *resx* hinzufügen. eine `EmbeddedResource` -Element, enthält eine `MergeWithCTO` Element, wie im folgenden Beispiel dargestellt:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Dieses Markup gesendet werden sollen, in der `ItemGroup` -Element, das eingebettete Ressourcen enthält.

4.  Öffnen Sie die Paketdatei, die in der Regel mit dem Namen  *\<ProjectName\>Package.cs* oder  *\<ProjectName\>Package.vb*, im Editor.

5.  Hinzufügen einer `ProvideMenuResource` -Attribut auf die Paketklasse und, wie im folgenden Beispiel gezeigt.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Der Wert des erste Parameters muss dem Wert des entsprechen den `ResourceName` Attribut, das Sie in der Projektdatei definiert.

## <a name="see-also"></a>Siehe auch
- [Erstellen von VSCT-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)