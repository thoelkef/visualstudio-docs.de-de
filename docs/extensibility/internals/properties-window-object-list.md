---
title: Eigenschaften Fenster Objektliste | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706150"
---
# <a name="properties-window-object-list"></a>Objektliste des Eigenschaftenfensters
Die Objektliste im **Eigenschaftenfenster** ist eine Dropdownliste, mit der Sie die Auswahl in andere Objekte ändern können, die in einem oder mehreren ausgewählten Fenstern verfügbar sind. Wenn Sie ein anderes Objekt aus dieser <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> Liste auswählen, wird ein Aufruf ausgelöst, um die Umgebung darüber zu informieren, dass ein neues Objekt ausgewählt wurde. Die im **Fenster Eigenschaften** angezeigten Informationen werden dann geändert, um die Eigenschaften anzuzeigen, die dem neu ausgewählten Objekt zugeordnet sind.

## <a name="the-object-list"></a>Die Objektliste
 Die Objektliste besteht aus zwei Feldern: dem Objektnamen (fett dargestellt) und dem Objekttyp.

 Der Objektname, der links neben dem Objekttyp in Fettschrift `Name` angezeigt wird, wird aus dem Objekt selbst mithilfe der von der <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> Schnittstelle bereitgestellten Eigenschaft abgerufen. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, die einzige <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>Methode <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> für , gibt für die Coclass dieser Schnittstelle zurück. Das **Eigenschaftenfenster** verwendet, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> um den Namen der coclass abzubekommen, der als Objektname in der Dropdownliste angezeigt wird.

 Wenn das Objekt nicht `Name` über eine Eigenschaft verfügt, wird im Bereich Name der Objektliste kein Name angezeigt. Sie können dem Objekt eine Name-Eigenschaft hinzufügen, wenn der Name in der Objektliste angezeigt werden soll.

 Wenn das COM-Objekt <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>nicht implementiert wird, zeigt das **Eigenschaftenfenster** den Schnittstellennamen anstelle des Objektnamens auf der linken Seite der Liste an.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
