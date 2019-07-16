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
ms.openlocfilehash: 01d004491feedff26c350cd7d40c544bc6b6de0f
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "64783750"
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

## <a name="remarks"></a>Hinweise
 Symboleigenschaften für die virtuelle Adresse (VA) werden mithilfe des Werts für diese Methode berechnet. Virtuelle Adressen werden nicht berechnet werden, es sei denn, diese Eigenschaft nicht 0 (null) festgelegt ist.

> [!NOTE]
> Sie müssen diese Methode aufrufen, wenn Sie erhalten die [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt aus, und bevor Sie beginnen mit dem Objekt, wenn Sie keine virtuellen Eigenschaften von Symbolen verwenden müssen.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)