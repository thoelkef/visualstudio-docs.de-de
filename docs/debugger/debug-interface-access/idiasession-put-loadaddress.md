---
title: 'Idiasession:: Put_loadaddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b768b06e0702f7929b402086dcc6e11918f3e683
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630092"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Legt die Ladeadresse für die ausführbare Datei, die entspricht auf die Symbole in diesem Symbolspeicher fest.

## <a name="syntax"></a>Syntax

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parameter
 `NewVal`

[in] Lädt die Adresse für die ausführbare Datei.

## <a name="remarks"></a>Anmerkungen
 Symboleigenschaften für die virtuelle Adresse (VA) werden mithilfe des Werts für diese Methode berechnet. Virtuelle Adressen werden nicht berechnet werden, es sei denn, diese Eigenschaft nicht 0 (null) festgelegt ist.

> [!NOTE]
>  Sie müssen diese Methode aufrufen, wenn Sie erhalten die [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt aus, und bevor Sie beginnen mit dem Objekt, wenn Sie keine virtuellen Eigenschaften von Symbolen verwenden müssen.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)