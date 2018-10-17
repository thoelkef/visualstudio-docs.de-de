---
title: 'Vorgehensweise: Erstellen Sie ein. VSCT-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b28fe38a9d45816481233c3ae267b3c764ee264
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186668"
---
# <a name="how-to-create-a-vsct-file"></a>Vorgehensweise: Erstellen Sie ein. VSCT-Datei
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es gibt mehrere Möglichkeiten, eine XML-basierte Visual Studio Command Table-Konfigurationsdatei (VSCT) zu erstellen.  
  
-   Sie können in ein neues VSPackage erstellen, die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Paket-Vorlage.  
  
-   Sie können den XML-basierten Befehl Table Configuration-Compiler Vsct.exe, verwenden, um eine Datei aus einer vorhandenen CTC-Datei zu generieren.  
  
-   Sie können die Vsct.exe verwenden, um eine VSCT-Datei aus einer vorhandenen CTO-Datei zu generieren.  
  
-   Sie können eine neue VSCT-Datei manuell erstellen.  
  
 In diesem Thema wird erläutert, wie Sie eine neue VSCT-Datei manuell zu erstellen.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>So erstellen Sie eine neue VSCT-Datei manuell  
  
1.  Starten Sie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
2.  Auf der **Datei** Startmenü **neu**, und klicken Sie dann auf **Datei**.  
  
3.  In der **Vorlagen** Bereich, klicken Sie auf **XML-Datei** , und klicken Sie dann auf **öffnen**.  
  
4.  Auf der **Ansicht** Menü klicken Sie auf **Fenster "Eigenschaften"** zum Anzeigen der Eigenschaften der XML-Datei.  
  
5.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche zum Durchsuchen (...) für die Schemas-Eigenschaft.  
  
6.  Wählen Sie in der Liste der XSD-Schemas das vsct.xsd-Schema. Wenn es sich nicht in der Liste ist, klicken Sie auf **hinzufügen** und suchen Sie dann die Datei auf einem lokalen Laufwerk. Klicken Sie auf **OK** Wenn Sie fertig sind.  
  
7.  Geben Sie in der XML-Datei, `<CommandTable` und drücken Sie dann die Registerkarte. Schließen Sie das Tag, indem Sie eingeben `>`.  
  
     Dadurch wird eine grundlegende VSCT-Datei erstellt.  
  
8.  Geben Sie die Elemente der XML-Datei, die Sie hinzufügen möchten, die gemäß der [VSCT Schema](../../extensibility/vsct-xml-schema-reference.md). Weitere Informationen finden Sie unter [Authoring. VSCT-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Einfach eine VSCT-Datei hinzufügen, zu einem Projekt bewirkt nicht kompilieren. Sie müssen es im Buildprozess integrieren.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Projekt-Kompilierung einer VSCT-Datei hinzu  
  
1.  Öffnen Sie die Projektdatei im Editor. Wenn das Projekt geladen wird, müssen Sie es zunächst entladen.  
  
2.  Hinzufügen einer [ItemGroup-Element](../../msbuild/itemgroup-element-msbuild.md) , das eine VSCTCompile-Element enthält, wie im folgenden Beispiel gezeigt.  
  
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
  
     Dieses Markup funktionieren im ItemGroup-Element, das eingebettete Ressourcen enthält.  
  
4.  Öffnen Sie die Paketdatei, die in der Regel mit dem Namen *ProjectName*Package.cs oder *ProjectName*Package.vb, im Editor.  
  
5.  Fügen Sie für die Paketklasse ein ProvideMenuResource-Attribut hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Der Wert des erste Parameters muss es sich um den Wert des Attributs ResourceName übereinstimmen, die Sie in der Projektdatei definiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen. VSCT-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTC-Datei](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Vorgehensweise: Erstellen Sie ein. VSCT-Datei aus einem vorhandenen. CTO-Datei](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)

