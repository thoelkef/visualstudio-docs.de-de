---
title: "Liste der Eigenschaften im Fenster Objekt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Im Eigenschaftenfenster-Liste"
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Liste der Eigenschaften im Fenster Objekt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Objektliste im **Eigenschaften** Fenster ist eine Dropdownliste. Auf diese Weise können Sie die Auswahl auf andere Objekte zu ändern, die in einer oder mehreren ausgewählten Fenster verfügbar sind.  Das Auswählen eines anderen Objekts aus dieser Liste startet einen Aufruf des <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> , um die Umgebungen zu informieren, dass ein neues Objekt ausgewählt wurde.  Die Informationen, die im **Eigenschaften** Fenster angezeigt werden, werden dann geändert, um die Eigenschaften anzuzeigen, die dem neu ausgewählte Objekt beziehen.  
  
## Die Objektliste  
 Die Objektliste besteht aus zwei Feldern: Der Objektname \(in Fettschrift angezeigt\) und der Objekttyp.  
  
 Der Objektname, der auf der linken Seite des Objekttyps in Fettschrift angezeigt wird, wird das Objekt selbst mit der `Name`\-Eigenschaft abgerufen, die von der <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>\-Schnittstelle.  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>die einzige Möglichkeit, auf <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, gibt <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> für die Co\-Klasse dieser Schnittstelle zurück.  Das **Eigenschaften** Fenster verwendet <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , um den Namen der Co\-Klasse abzurufen, die als der Objektname in der Dropdownliste angezeigt wird.  
  
 Wenn das Objekt keine `Name`\-Eigenschaft verfügt, wird kein Name der Objektliste im Bereich Name angezeigt.  Sie können eine Namenseigenschaft dem Objekt hinzufügen, wenn Sie den Namen, der in der Objektliste angezeigt wird.  
  
 Wenn das COM\-Objekt <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>nicht implementiert, wird das **Eigenschaften** Fenster den Schnittstellennamen anstelle des Objektnamens links neben der Liste an.  
  
## Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)