---
title: 'Vorgehensweise: Erstellen einer. Vsct-Datei | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158352"
---
# <a name="how-to-create-a-vsct-file"></a>Gewusst wie: Erstellen einer VSCT-Datei
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es gibt mehrere Möglichkeiten, eine XML-basierte Visual Studio-Befehls Tabellen Konfigurationsdatei (vsct-Datei) zu erstellen.  
  
- Sie können ein neues VSPackage in der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Paket Vorlage erstellen.  
  
- Sie können den XML-basierten Befehls Tabellen Konfigurations Compiler (Vsct.exe) verwenden, um eine Datei aus einer vorhandenen CTC-Datei zu generieren.  
  
- Sie können Vsct.exe verwenden, um eine vsct-Datei aus einer vorhandenen CTO-Datei zu generieren.  
  
- Sie können eine neue vsct-Datei manuell erstellen.  
  
  In diesem Thema wird erläutert, wie eine neue vsct-Datei manuell erstellt wird.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>So erstellen Sie manuell eine neue vsct-Datei  
  
1. Starten Sie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Datei**.  
  
3. Klicken Sie im Bereich **Vorlagen** auf **XML-Datei** , und klicken Sie dann auf **Öffnen**.  
  
4. Klicken Sie im Menü **Ansicht** auf **Eigenschaften Fenster** , um die Eigenschaften der XML-Datei anzuzeigen.  
  
5. Klicken Sie im **Eigenschaften** Fenster in der Eigenschaft Schemas auf die Schaltfläche zum Durchsuchen (...).  
  
6. Wählen Sie in der Liste der XSD-Schemas das Schema vsct. xsd aus. Wenn Sie nicht in der Liste enthalten ist, klicken Sie auf **Hinzufügen** , und suchen Sie dann die Datei auf einem lokalen Laufwerk. Klicken Sie anschließend auf **OK**.  
  
7. Geben Sie in der XML-Datei ein, `<CommandTable` und drücken Sie dann TAB. Schließen Sie das-Tag, indem Sie eingeben `>` .  
  
     Dadurch wird eine einfache vsct-Datei erstellt.  
  
8. Füllen Sie die Elemente der XML-Datei, die Sie hinzufügen möchten, gemäß dem [vsct-Schema](../../extensibility/vsct-xml-schema-reference.md)aus. Weitere Informationen finden Sie unter [Authoring. Vsct-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Das einfache Hinzufügen einer vsct-Datei zu einem Projekt führt nicht zu einer Kompilierung. Sie müssen Sie in den Buildprozess integrieren.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>So fügen Sie eine vsct-Datei zur Projekt Kompilierung hinzu  
  
1. Öffnen Sie die Projektdatei im Editor. Wenn das Projekt geladen ist, müssen Sie es zuerst entladen.  
  
2. Fügen Sie ein [ItemGroup-Element](../../msbuild/itemgroup-element-msbuild.md) hinzu, das ein VSCTCompile-Element enthält, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Das resourceName-Element sollte immer auf festgelegt sein `Menus.ctmenu` .  
  
3. Wenn das Projekt eine RESX-Datei enthält, fügen Sie ein EmbeddedResource-Element hinzu, das ein mergewithcto-Element enthält, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Dieses Markup sollte sich innerhalb des ItemGroup-Elements befinden, das eingebettete Ressourcen enthält.  
  
4. Öffnen Sie die Paketdatei, die in der Regel *ProjectName*Package.cs oder *ProjectName*Package. vb heißt, im Editor.  
  
5. Fügen Sie der Package-Klasse ein providemenuresource-Attribut hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Der erste Parameterwert muss mit dem Wert des resourceName-Attributs, das Sie in der Projektdatei definiert haben, identisch sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellungs. Vsct-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio-Befehls Tabelle (. Vsct-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Vorgehensweise: Erstellen einer. Vsct-Datei aus einer vorhandenen. CTC-Datei](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Vorgehensweise: Erstellen einer. Vsct-Datei aus einer vorhandenen. CTO-Datei](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)
