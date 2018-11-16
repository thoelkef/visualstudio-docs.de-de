---
title: Objektliste des Eigenschaftenfensters | Microsoft-Dokumentation
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
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bbb9153a216b2d2fcc7cdeba0399aa60fc73881e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768911"
---
# <a name="properties-window-object-list"></a>Objektliste des Eigenschaftenfensters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In der Liste der **Eigenschaften** Fenster ist eine Dropdown-Liste, die Ihnen ermöglicht, ändern die Auswahl auf andere Objekte innerhalb von ein oder mehrere ausgewählte Windows zur Verfügung. Ein anderes Objekt aus, in der Liste auswählen, startet einen Aufruf an <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> um der Umgebung zu informieren, dass ein neues Objekt ausgewählt wurde. Die Informationen den **Eigenschaften** Fenster wird dann geändert, um das neu ausgewählte Objekt zugeordneten Eigenschaften anzuzeigen.  
  
## <a name="the-object-list"></a>Objektliste  
 Die Objektliste besteht aus zwei Feldern: der Objektname (in Fettschrift angezeigt) und -Objekttyp vorliegt.  
  
 Der Objektname, der auf der linken Seite des Objekttyps in Fettschrift angezeigt wird abgerufen, von das Objekt selbst mit dem `Name` von bereitgestellte Eigenschaft der <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> Schnittstelle. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, die einzige Methode auf <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, gibt <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> für diese Schnittstelle für die Co-Klasse. Die **Eigenschaften** Fenster verwendet <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> zum Abrufen des Namens der Co-Klasse, die als der Objektname in der Dropdown-Liste angezeigt wird.  
  
 Wenn das Objekt keine `Name` Eigenschaft, einen Namen wird nicht im Bereich der Objektliste angezeigt. Sie können auf das Objekt eine Name-Eigenschaft hinzufügen, wenn Sie den Namen in der Liste angezeigt werden soll.  
  
 Wenn das COM-Objekt nicht implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **Eigenschaften** Fenster werden die Namen der Schnittstelle anstelle des Objektnamens auf der linken Seite der Liste angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)

