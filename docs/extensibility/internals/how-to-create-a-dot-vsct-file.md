---
title: 'Gewusst wie: Erstellen einer . Vsct-Datei | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5a5f53ec87c9447af232e9d0528108ddbaea01a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708108"
---
# <a name="how-to-create-a-vsct-file"></a>Gewusst wie: Erstellen einer .vsct-Datei

Es gibt mehrere Möglichkeiten, eine XML-basierte Visual Studio-Befehlstabellenkonfiguration (*.vsct*) zu erstellen.

- Sie können ein neues VSPackage in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Paketvorlage erstellen.

- Sie können den XML-basierten Befehlstabellenkonfigurationscompiler *Vsct.exe*verwenden, um eine Datei aus einer vorhandenen *CTC-Datei* zu generieren.

- Sie können *Vsct.exe* verwenden, um eine *.vsct-Datei* aus einer vorhandenen *Cto-Datei* zu generieren.

- Sie können manuell eine neue *.vsct-Datei* erstellen.

  In diesem Artikel wird erläutert, wie Sie manuell eine neue *.vsct-Datei* erstellen.

### <a name="to-manually-create-a-new-vsct-file"></a>So erstellen Sie manuell eine neue .vsct-Datei

1. Starten Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Datei**.

3. Klicken Sie im Bereich **Vorlagen** auf **XML-Datei** und dann auf **Öffnen**.

4. Klicken Sie im Menü **Ansicht** auf **Eigenschaften,** um die Eigenschaften der XML-Datei anzuzeigen.

5. Klicken Sie im **Eigenschaftenfenster** auf die Schaltfläche **Durchsuchen** in der **Schemas-Eigenschaft.**

6. Wählen Sie in der Liste der XSD-Schemas das Schema *vsct.xsd* aus. Wenn es nicht in der Liste ist, klicken Sie auf **Hinzufügen** und suchen Sie die Datei dann auf einem lokalen Laufwerk. Klicken Sie anschließend auf **OK**.

7. Geben Sie in der XML-Datei *<CommandTable* ein, und **drücken**Sie dann tab . Schließen Sie das *>* Tag, indem Sie eingeben.

    Mit dieser Aktion wird eine grundlegende *.vsct-Datei* erstellt.

8. Füllen Sie die Elemente der XML-Datei aus, die Sie gemäß dem [VSCT-XML-Schemaverweis](../../extensibility/vsct-xml-schema-reference.md)hinzufügen möchten. Weitere Informationen finden Sie unter [Author .vsct-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Gewusst wie: Erstellen einer .vsct-Datei aus einer vorhandenen CTC-Datei

Sie können eine XML-basierte *.vsct-Datei* aus einer vorhandenen Befehlstabelle *.ctc-Quelldatei* erstellen. Dabei können Sie das neue XML-basierte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Command Table-Compilerformat (VSCT) nutzen.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTC-Datei

1. Rufen Sie eine Kopie der Sprache Perl ab.

2. Rufen Sie eine Kopie des Perl-Skripts *ConvertCTCToVSCT.pl*ab, der sich in der * \<Regel im Installationspfad des Visual Studio SDK befindet,> Ordner "VisualStudioIntegration" und "Tools"* und "Bin".

3. Rufen Sie eine Kopie der *.ctc-Quelldatei* ab, die Sie konvertieren möchten.

4. Speichern Sie die Dateien im selben Verzeichnis.

5. Navigieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sie im Eingabeaufforderungsfenster zum Verzeichnis.

6. type

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    wobei *PkgCmd.ctc* der Name der *.ctc-Datei* und *PkgCmd.vsct* der Name der *.vsct-Datei* ist, die Sie erstellen möchten.

    Mit dieser Aktion wird eine neue *.vsct* XML-Befehlstabellenquelldatei erstellt. Sie können die Datei mit *Vsct.exe*, dem VSCT-Compiler, wie jede andere *.vsct-Datei* kompilieren.

   > [!NOTE]
   > Sie können die Lesbarkeit der *.vsct-Datei* verbessern, indem Sie die XML-Kommentare neu formatieren.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Gewusst wie: Erstellen einer .vsct-Datei aus einer vorhandenen Cto-Datei

Sie können eine XML-basierte *.vsct-Datei* aus einer vorhandenen binären *.cto-Datei* erstellen. Diese Vorgehensweise ermöglicht es Ihnen, das neue Befehlstabellen-Compilerformat zu nutzen. Dieser Vorgang funktioniert auch dann, wenn die *Cto-Datei* aus einer *.ctc-Datei* kompiliert wurde. Sie können die *.vsct-Datei* bearbeiten und in eine andere Cto-Datei kompilieren.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTO-Datei

1. Erhalten Sie Kopien der *.cto-Datei* und der entsprechenden *.ctsym-Datei.*

2. Platzieren Sie die Dateien in demselben Verzeichnis wie der *vsct.exe-Compiler.*

3. Wechseln Sie in der Eingabeaufforderung für den Befehl Visual Studio zu dem Verzeichnis, das die *Dateien .cto* und *.ctsym* enthält.

4. type

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     wobei \<\> ctofilename der Name der *.cto-Datei* ist, \<vsctfilename\> der Name der *.vsct-Datei,* die Sie erstellen möchten, \<und symfilename\> ist der Name der *.ctsym-Datei.*

     Dieser Prozess erstellt eine neue *.vsct* XML-Befehlstabellen-Compilerdatei. Sie können die Datei mit *vsct.exe*, dem vsct-Compiler, wie jede andere *.vsct-Datei* bearbeiten und kompilieren.

## <a name="compile-the-code"></a>Kompilieren des Codes
 Das einfache Hinzufügen einer *.vsct-Datei* zu einem Projekt führt nicht dazu, dass es kompiliert wird. Sie müssen sie in den Buildprozess integrieren.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>So fügen Sie eine .vsct-Datei zur Projektkompilierung hinzu

1. Öffnen Sie die Projektdatei im Editor. Wenn das Projekt geladen wird, müssen Sie es zuerst entladen.

2. Fügen Sie ein [ItemGroup-Element](../../msbuild/itemgroup-element-msbuild.md) hinzu, das ein `VSCTCompile` Element enthält, wie im folgenden Beispiel gezeigt.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     Das `ResourceName` Element sollte immer `Menus.ctmenu`auf festgelegt werden.

3. Wenn Ihr Projekt eine *.resx-Datei* enthält, fügen Sie ein `EmbeddedResource` Element hinzu, das ein `MergeWithCTO` Element enthält, wie im folgenden Beispiel gezeigt:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Dieses Markup sollte `ItemGroup` innerhalb des Elements gehen, das eingebettete Ressourcen enthält.

4. Öffnen Sie die Paketdatei mit dem Normalerweisenamen * \<ProjectName\>Package.cs* oder * \<ProjectName\>Package.vb*im Editor.

5. Fügen `ProvideMenuResource` Sie der Paketklasse ein Attribut hinzu, wie im folgenden Beispiel gezeigt.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Der erste Parameterwert muss mit `ResourceName` dem Wert des Attributs übereinstimmen, das Sie in der Projektdatei definiert haben.

## <a name="see-also"></a>Weitere Informationen
- [Author .vsct-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio-Befehlstabellendateien (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)
