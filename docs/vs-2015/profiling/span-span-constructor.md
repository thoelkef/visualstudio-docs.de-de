---
title: 'span:: span-Konstruktor | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df6df731de90a9aad9e6cc637b3f218e481b66b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198295"
---
# <a name="spanspan-constructor"></a>span::span-Konstruktor

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Initialisiert eine neue Instanz der `span`-Klasse.

## <a name="syntax"></a>Syntax

```
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parameter

`_Series`: gültiger Markerreihenkontext.

`_Format`: eine zusammengesetzte Formatzeichenfolge mit Text, der „0“ (null) oder mehr Formatelemente enthält, die Objekten in der Argumentliste entsprechen.

`_Importance`: die Wichtigkeitsstufe.

`_Category`: die Kategorie.

## <a name="requirements"></a>Anforderungen

**Header:** cvmarkersobj.h

**Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Weitere Informationen

[Span-Klasse](../profiling/span-class.md)
