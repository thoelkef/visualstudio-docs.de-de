---
title: "Gewusst wie: Ausw&#228;hlen der zu verwendenden XML-Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Ausw&#228;hlen der zu verwendenden XML-Schemas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der XML\-Editor stellt einen Schemacache im Verzeichnis "%InstallDir%\\Xml\\Schemas" bereit.Der Schemacache enthält bekannte XML\-Schemata, die für IntelliSense und zur Überprüfung von XML\-Dokumenten verwendet werden.  
  
 Mithilfe der Dokumenteigenschaft **Schemas** werden die zu verwendenden Schemas der XML Schema Definition Language \(XSD\) ausgewählt.Sie können damit Schemas aus dem Schemacache auswählen oder ein Schema angeben, das sich nicht im Cache befindet.  
  
 Die von Ihnen ausgewählten Schemas werden zusammen mit den anderen XML\-Dokumenteigenschaften in der versteckten Projektmappen\-Benutzeroptionendatei \(.suo\) abgespeichert.Daher müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.  
  
> [!NOTE]
>  Der Editor kann mithilfe eines Inlineschemas oder eines Schemas, auf das von dem `xsd:schemaLocation`\-Attribut verwiesen wird, die Validierung vornehmen.Weitere Informationen finden Sie unter [Validierung von XML\-Dokumenten](../xml-tools/xml-document-validation.md).  
  
### So wählen Sie ein XML\-Schema aus dem Schemacache aus  
  
1.  Öffnen Sie eine Datei im XML\-Editor.  
  
2.  Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Schemata** auf die Schaltfläche.  
  
     Das Dialogfeld **XML\-Schemata** wird angezeigt.Im Dialogfeld werden alle Schemata mit einer XSD\-Erweiterung im Schemacache aufgelistet \(einschließlich Schemata, auf die in catalog.xml verwiesen wird\) sowie alle Schemata, die sich in der aktuellen Projektmappe befinden, die in Visual Studio geöffnet sind bzw. auf die in einem `xsd:schemaLocation`\-Attribut oder in der **Schemas**\-Eigenschaft verwiesen wird.  
  
3.  Wählen Sie Schemata zu Validierungszwecken aus, indem Sie eine der folgenden Methoden verwenden:  
  
    -   Wählen Sie ein im Dialogfeld **XML\-Schemas** aufgelistetes Schema aus, klicken Sie auf die Spalte **Verwendung**, und wählen Sie dann **Dieses Schema verwenden** aus.  
  
     – oder –  
  
    -   Wählen Sie mehrere im Dialogfeld **XML\-Schemas** aufgelistete Schemas aus, betätigen Sie die rechte Maustaste, und wählen Sie **Dieses Schema verwenden** aus.  
  
4.  Klicken Sie auf **OK**.  
  
     Die Liste der ausgewählten Schemata wird zurück in die **Schemas**\-Eigenschaft des Dokuments kopiert.  
  
### So fügen Sie dem Schemacache ein XML\-Schema hinzu  
  
1.  Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Schemas** auf die Schaltfläche.  
  
2.  Klicken Sie auf **Hinzufügen**.  
  
     Dadurch wird das Dialogfeld **XSD\-Schema öffnen** geöffnet.  
  
3.  Navigieren Sie zu den Schemas, die dem Schemacache hinzugefügt werden sollen, und markieren Sie diese.  
  
4.  Klicken Sie auf **Öffnen**.  
  
     Die Schemas werden dem Schemacache hinzugefügt, und der Wert der Spalte **Verwendung** wird auf **Dieses Schema verwenden** eingestellt.  
  
### So löschen Sie ein XML\-Schema aus dem Schemacache  
  
1.  Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Schemas** auf die Schaltfläche.  
  
2.  Markieren Sie das zu entfernende Schema, und klicken Sie auf **Entfernen**.  
  
     Das Schema wird aus dem In\-Memory\-Schemacache , jedoch nicht aus dem Dateisystem entfernt.  
  
    > [!NOTE]
    >  Wenn mit einem `schemaLocation`\-Attribut oder einem entsprechenden `targetNamespace` auf das Schema verwiesen wird, kann es aufgrund der automatischen Zuordnung nicht über **Entfernen** entfernt werden.In diesem Fall sollten Sie das Schema in der Spalte **Verwendung** auf **Ausgewählte Schemas nicht verwenden** festlegen.  
  
## Siehe auch  
 [Schemacache](../xml-tools/schema-cache.md)   
 [XML\-Schemata \(Dialogfeld\)](../xml-tools/xml-schemas-dialog-box.md)   
 [XML\-Editor](../xml-tools/xml-editor.md)