---
title: Xml (dynamische XElement-Eigenschaft) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663844"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (dynamische XElement-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ruft den unformatierten XML-Inhalt des Elements ab.

## <a name="syntax"></a>Syntax

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert
 <xref:System.String>, die den unformatierten XML-Inhalt des Elements darstellt.

## <a name="remarks"></a>Bemerkungen
 Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29>-Methode der <xref:System.Xml.Linq.XNode?displayProperty=fullName>-Klasse, wobei der `SaveOptions`-Parameter auf <xref:System.Xml.Linq.SaveOptions> festgelegt ist.

## <a name="see-also"></a>Weitere Informationen
 [Wert](../designers/value-xelement-dynamic-property.md) für [dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)
