---
title: 'Idiasession:: Put_loadaddress | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cec66d9d7287c6432c02c0ec2a1c38f903811c44
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259454"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt die Ladeadresse für die ausführbare Datei, die entspricht auf die Symbole in diesem Symbolspeicher fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
>  Sie müssen diese Methode aufrufen, wenn Sie erhalten die [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt aus, und bevor Sie beginnen mit dem Objekt, wenn Sie keine virtuellen Eigenschaften von Symbolen verwenden müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



