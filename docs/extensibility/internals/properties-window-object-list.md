---
title: Objektliste "Eigenschaften Fenster" | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e50b3fe46edb8d14cad9a03a45bc8650cb9713ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725184"
---
# <a name="properties-window-object-list"></a>Objektliste des Eigenschaftenfensters
Die Objektliste im **Eigenschaften** Fenster ist eine Dropdown Liste, mit der Sie die Auswahl in andere Objekte ändern können, die in einem oder mehreren ausgewählten Fenstern verfügbar sind. Wenn Sie ein anderes Objekt aus dieser Liste auswählen, wird ein <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> aufgerufen, um der Umgebung mitzuteilen, dass ein neues Objekt ausgewählt wurde. Die im **Eigenschaften** Fenster angezeigten Informationen werden dann geändert, um die Eigenschaften anzuzeigen, die dem neu ausgewählten Objekt zugeordnet sind.

## <a name="the-object-list"></a>Die Objektliste
 Die Objektliste besteht aus zwei Feldern: dem Objektnamen (fett angezeigt) und dem Objekttyp.

 Der im fett formatierten Objekttyp angezeigte Objektname wird aus dem Objekt selbst abgerufen. dabei wird die `Name`-Eigenschaft verwendet, die von der <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>-Schnittstelle bereitgestellt wird. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, die einzige Methode auf <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, wird <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> für die Co-Klasse dieser Schnittstelle zurückgegeben. Im **Eigenschaften** Fenster wird <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> verwendet, um den Namen der Co-Klasse zu erhalten, die in der Dropdown Liste als Objektname angezeigt wird.

 Wenn das Objekt nicht über eine `Name`-Eigenschaft verfügt, wird ein Name nicht im namens Bereich der Objektliste angezeigt. Sie können dem-Objekt eine Name-Eigenschaft hinzufügen, wenn der Name in der Objektliste angezeigt werden soll.

 Wenn das COM-Objekt <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> nicht implementiert, zeigt das **Eigenschaften** Fenster den Schnittstellennamen anstelle des Objekt namens auf der linken Seite der Liste an.

## <a name="see-also"></a>Siehe auch
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)