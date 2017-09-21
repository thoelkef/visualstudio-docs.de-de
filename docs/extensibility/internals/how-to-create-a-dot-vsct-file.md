---
title: "Gewusst wie: Erstellen einer. VSCT-Datei | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT-Dateien erstellen"
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Erstellen einer. VSCT-Datei
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Es gibt mehrere Methoden zum Erstellen einer XML\-basierte Visual Studio\-Befehlstabelle\-Konfigurationsdatei \(VSCT\).  
  
-   Sie können in einem neuen VSPackage erstellen die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Paketvorlage.  
  
-   Die XML\-basierten Befehl Tabelle Configuration\-Compiler Vsct.exe, können Sie um eine Datei aus einer vorhandenen .ctc\-Datei zu generieren.  
  
-   Vsct.exe können zum Generieren einer VSCT\-Datei aus einer vorhandenen .cto\-Datei.  
  
-   Sie können eine neue VSCT\-Datei manuell erstellen.  
  
 In diesem Thema erläutert, wie eine neue VSCT\-Datei manuell erstellen.  
  
### So erstellen Sie eine neue VSCT\-Datei manuell  
  
1.  Starten Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Auf der **Datei** auf **Neu**, und klicken Sie dann auf **Datei**.  
  
3.  In der **Vorlagen** Bereich, klicken Sie auf **XML\-Datei** und klicken Sie dann auf **Öffnen**.  
  
4.  Auf der **Ansicht** Menü klicken Sie auf **Eigenschaftenfenster** die Eigenschaften der XML\-Datei angezeigt.  
  
5.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche zum Durchsuchen \(...\) Schaltfläche in der Eigenschaft Schemas.  
  
6.  Wählen Sie in der Liste der XSD\-Schemas das vsct.xsd\-Schema. Wenn es nicht in der Liste enthalten ist, klicken Sie auf **Hinzufügen** und dann die Datei auf einem lokalen Laufwerk. Klicken Sie auf **OK** Wenn Sie fertig sind.  
  
7.  Geben Sie in der XML\-Datei `<CommandTable` und die Tabulatortaste drücken. Schließen Sie das Tag durch Eingabe `>`.  
  
     Dadurch wird eine grundlegende VSCT\-Datei erstellt.  
  
8.  Geben Sie in den Elementen der XML\-Datei, die Sie hinzufügen möchten, und gemäß der [VSCT\-Schema](../../extensibility/vsct-xml-schema-reference.md). Weitere Informationen finden Sie unter [Erstellen. VSCT\-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## Kompilieren des Codes  
 Einfach zu einem Projekt hinzufügen einer VSCT\-Datei bewirkt nicht kompilieren. Sie müssen es im Buildprozess einschließen.  
  
### Kompilieren des Projekts eine VSCT\-Datei hinzu  
  
1.  Öffnen Sie die Projektdatei im Editor. Wenn das Projekt geladen wird, müssen Sie es zunächst entladen.  
  
2.  Hinzufügen einer [ItemGroup\-Element](../../msbuild/itemgroup-element-msbuild.md) ein VSCTCompile\-Element enthält, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName\-Element sollte immer auf festgelegt werden `Menus.ctmenu`.  
  
3.  Wenn das Projekt eine RESX\-Datei enthält, fügen Sie EmbeddedResource Element, das ein Element MergeWithCTO enthält hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Dieses Markup sollte in ItemGroup\-Element eingefügt, das eingebettete Ressourcen enthält.  
  
4.  Öffnen Sie die Paketdatei in der Regel mit der Bezeichnung *Projektname*Package.cs oder *Projektname*Package.vb, im Editor.  
  
5.  Fügen Sie ein ProvideMenuResource\-Attribut für die Paketklasse, wie im folgenden Beispiel dargestellt.  
  
    ```c#  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     Der erste Parameterwert muss den Wert des Attributs ResourceName übereinstimmen, die Sie in der Projektdatei definiert.  
  
## Siehe auch  
 [Erstellen. VSCT\-Dateien](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Gewusst wie: Erstellen einer VSCT\-Datei anhand einer vorhandenen CTC\-Datei](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Gewusst wie: Erstellen einer VSCT\-Datei anhand einer vorhandenen CTO\-Datei](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT XML\-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)