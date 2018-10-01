---
title: 'Idiasession:: Put_loadaddress | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: e39ac68468113f371c032f2f29b4613fa229a3b7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511805"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasession:: Put_loadaddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-put-loadaddress).  
  
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



