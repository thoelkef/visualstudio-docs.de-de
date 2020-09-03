---
title: Objektliste "Eigenschaften Fenster" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95ef509491e05daf575e211ae479c815994eb3d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148333"
---
# <a name="properties-window-object-list"></a>Objektliste des Eigenschaftenfensters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Objektliste im **Eigenschaften** Fenster ist eine Dropdown Liste, mit der Sie die Auswahl in andere Objekte ändern können, die in einem oder mehreren ausgewählten Fenstern verfügbar sind. Wenn Sie ein anderes Objekt aus dieser Liste auswählen, wird ein Rückruf von ausgelöst <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> , um die Umgebung darüber zu informieren, dass ein neues-Objekt ausgewählt wurde. Die im **Eigenschaften** Fenster angezeigten Informationen werden dann geändert, um die Eigenschaften anzuzeigen, die dem neu ausgewählten Objekt zugeordnet sind.  
  
## <a name="the-object-list"></a>Die Objektliste  
 Die Objektliste besteht aus zwei Feldern: dem Objektnamen (fett angezeigt) und dem Objekttyp.  
  
 Der im fett formatierten Objekttyp angezeigte Objektname wird aus dem Objekt selbst abgerufen, wobei die `Name` von der Schnittstelle bereitgestellte Eigenschaft verwendet wird <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> . <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, die einzige Methode für <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , gibt <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> für die Co-Klasse der Schnittstelle zurück. Im **Eigenschaften** Fenster wird verwendet, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> um den Namen der Co-Klasse zu erhalten, die als Objektname in der Dropdown Liste angezeigt wird.  
  
 Wenn das Objekt nicht über eine `Name` Eigenschaft verfügt, wird ein Name nicht im namens Bereich der Objektliste angezeigt. Sie können dem-Objekt eine Name-Eigenschaft hinzufügen, wenn der Name in der Objektliste angezeigt werden soll.  
  
 Wenn das COM-Objekt nicht implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , zeigt das **Eigenschaften** Fenster den Schnittstellennamen anstelle des Objekt namens auf der linken Seite der Liste an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
