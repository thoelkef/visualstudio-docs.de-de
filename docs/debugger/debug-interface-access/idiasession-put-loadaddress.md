---
title: 'Idiasession:: Put_loadaddress | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f4721ee818c4dc75d883c7accd2faa162521de13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
Legt die Adresse des für die entsprechende ausführbare Datei auf die Symbole in dieser Symbolspeicher fest.  
  
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
 Symboleigenschaften für die virtuelle Adresse ("VA" ist) werden mit dem Wert dieser Methode berechnet. Virtuelle Adressen sind nicht berechnet werden, es sei denn, diese Eigenschaft nicht 0 (null), um festgelegt ist.  
  
> [!NOTE]
>  Sie müssen diese Methode aufrufen, wenn Sie erhalten die [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt, und bevor Sie beginnen mit dem Objekt aus, wenn Sie virtuelle Eigenschaften verwenden, auf die Symbole müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)