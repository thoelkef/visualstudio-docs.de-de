---
title: 'Vorgehensweise: Erstellen Sie eine. Vsct-Datei | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3155ff69db461e652b11ff6e8ec6d405000244f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924183"
---
# <a name="how-to-create-a-vsct-file"></a>Vorgehensweise: Erstellen einer vsct-Datei

Es gibt mehrere Möglichkeiten, eine XML-basierte Visual Studio-Befehls Tabellen Konfigurationsdatei (*vsct*-Datei) zu erstellen.

- Sie können ein neues VSPackage in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Paket Vorlage erstellen.

- Sie können den XML-basierten Befehls Tabellen Konfigurations Compiler *vsct. exe*verwenden, um eine Datei aus einer vorhandenen *CTC* -Datei zu generieren.

- Sie können " *vsct. exe* " verwenden, um eine *vsct* -Datei aus einer vorhandenen *CTO* -Datei zu generieren.

- Sie können eine neue *vsct* -Datei manuell erstellen.

  In diesem Artikel wird erläutert, wie Sie eine neue *vsct* -Datei manuell erstellen.

### <a name="to-manually-create-a-new-vsct-file"></a>So erstellen Sie manuell eine neue vsct-Datei

1. Starten Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

2. Auf der **Datei** Startmenü **neu**, und klicken Sie dann auf **Datei**.

3. Klicken Sie im Bereich **Vorlagen** auf **XML-Datei** , und klicken Sie dann auf **Öffnen**.

4. Klicken Sie im Menü **Ansicht** auf **Eigenschaften** , um die Eigenschaften der XML-Datei anzuzeigen.

5. Klicken Sie im **Eigenschaften** Fenster in der Eigenschaft **Schemas** auf die Schaltfläche **Durchsuchen** .

6. Wählen Sie in der Liste der XSD-Schemas das Schema *vsct. xsd* aus. Wenn Sie nicht in der Liste enthalten ist, klicken Sie auf **Hinzufügen** , und suchen Sie dann die Datei auf einem lokalen Laufwerk. Wenn Sie fertig sind, klicken Sie auf **OK** .

7. Geben Sie in der XML-Datei *< commandtable* ein, und drücken Sie die **Tab**-Taste. Schließen Sie das-Tag *>* , indem Sie eingeben.

    Durch diese Aktion wird eine einfache *vsct* -Datei erstellt.

8. Füllen Sie die Elemente der XML-Datei aus, die Sie hinzufügen möchten, entsprechend der [vsct-XML-Schema Referenz](../../extensibility/vsct-xml-schema-reference.md). Weitere Informationen finden Sie unter Erstellen von [vsct-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md).

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Vorgehensweise: Erstellen einer vsct-Datei aus einer vorhandenen CTC-Datei

Sie können eine XML-basierte *vsct* -Datei aus einer vorhandenen *CTC* -Quelldatei der Befehls Tabelle erstellen. Dabei können Sie das neue XML-basierte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Command Table-Compilerformat (VSCT) nutzen.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTC-Datei

1. Rufen Sie eine Kopie der Sprache Perl ab.

2. Rufen Sie eine Kopie des Perl-Skripts *ConvertCTCToVSCT.pl*ab, das  *\<sich normalerweise im Visual Studio SDK-Installationspfad > Ordner \visualstudiointegration\tools\bin* befindet.

3. Rufen Sie eine Kopie der *CTC* -Quelldatei ab, die Sie konvertieren möchten.

4. Speichern Sie die Dateien im selben Verzeichnis.

5. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Navigieren Sie im Eingabe Aufforderungs Fenster zum Verzeichnis.

6. Typ

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    Dabei ist " *pkgcmd. CTC* " der Name der *CTC* -Datei, und " *pkgcmd. vsct* " ist der Name der *vsct* -Datei, die Sie erstellen möchten.

    Durch diese Aktion wird eine neue *vsct* -XML-Befehls Tabellen-Quelldatei erstellt. Sie können die Datei mit " *vsct. exe*", dem VSCT-Compiler, wie jede andere *vsct* -Datei kompilieren.

   > [!NOTE]
   > Sie können die Lesbarkeit der *vsct* -Datei verbessern, indem Sie die XML-Kommentare neu formatieren.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Vorgehensweise: Erstellen einer vsct-Datei anhand einer vorhandenen CTO-Datei

Sie können eine XML-basierte *vsct* -Datei aus einer vorhandenen binären *CTO* -Datei erstellen. Diese Vorgehensweise ermöglicht es Ihnen, das neue Befehlstabellen-Compilerformat zu nutzen. Dieser Prozess funktioniert auch dann, wenn die *CTO* -Datei aus einer *CTC* -Datei kompiliert wurde. Sie können die *vsct* -Datei bearbeiten und in eine andere CTO-Datei kompilieren.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>So erstellen Sie eine VSCT-Datei anhand einer CTO-Datei

1. Abrufen von Kopien der *CTO* -Datei und der entsprechenden *. ctsym* -Datei.

2. Platzieren Sie die Dateien im selben Verzeichnis wie der *vsct. exe* -Compiler.

3. Wechseln Sie an der Visual Studio-Eingabeaufforderung zu dem Verzeichnis, das die *CTO* -und *ctsym* -Dateien enthält.

4. Typ

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     wobei \<cdefilename\> der Name der *CTO* -Datei ist, \<ist vsctfilename\> der Name der *vsct* -Datei, die Sie erstellen möchten, und \<symfilename\> ist der Name von. die *. ctsym* -Datei.

     Bei diesem Vorgang wird eine neue *vsct* -XML-Befehls Tabellen-Compilerdatei erstellt. Sie können die Datei mit " *vsct. exe*", dem VSCT-Compiler, wie jede andere *vsct* -Datei bearbeiten und kompilieren.

## <a name="compile-the-code"></a>Kompilieren des Codes
 Das einfache Hinzufügen einer *vsct* -Datei zu einem Projekt führt nicht zu einer Kompilierung. Sie müssen Sie in den Buildprozess integrieren.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>So fügen Sie eine vsct-Datei zur Projekt Kompilierung hinzu

1. Öffnen Sie die Projektdatei im Editor. Wenn das Projekt geladen ist, müssen Sie es zuerst entladen.

2. Fügen Sie ein [ItemGroup-Element](../../msbuild/itemgroup-element-msbuild.md) hinzu `VSCTCompile` , das ein-Element enthält, wie im folgenden Beispiel gezeigt.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     Das `ResourceName` -Element sollte immer auf `Menus.ctmenu`festgelegt sein.

3. Wenn das Projekt eine *RESX* -Datei enthält, fügen Sie `EmbeddedResource` ein Element hinzu, `MergeWithCTO` das ein-Element enthält, wie im folgenden Beispiel gezeigt:

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     Dieses Markup sollte innerhalb des `ItemGroup` -Elements enthalten sein, das eingebettete Ressourcen enthält.

4. Öffnen Sie die Paketdatei, die in der Regel  *\<ProjectName\>Package.cs* oder  *\<ProjectName\>Package. vb*heißt, im Editor.

5. Fügen Sie `ProvideMenuResource` der Package-Klasse ein-Attribut hinzu, wie im folgenden Beispiel gezeigt.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     Der erste Parameterwert muss mit dem Wert des `ResourceName` -Attributs, das Sie in der Projektdatei definiert haben, identisch sein.

## <a name="see-also"></a>Siehe auch
- [Vsct-Dateien erstellen](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Vsct-Dateien (Visual Studio-Befehls Tabelle)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Vsct-XML-Schema Referenz](../../extensibility/vsct-xml-schema-reference.md)