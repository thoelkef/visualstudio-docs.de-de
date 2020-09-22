---
title: IDiaSession::p ut_loadAddress | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840828"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt die Lade Adresse für die ausführbare Datei fest, die den Symbolen in diesem Symbol Speicher entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `NewVal`  
 in Lade Adresse für die ausführbare Datei.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaften der Symbol-virtuellen Adresse (VA) werden mit dem Wert dieser Methode berechnet. Virtuelle Adressen werden nur berechnet, wenn diese Eigenschaft auf einen Wert ungleich 0 (null) festgelegt ist.  
  
> [!NOTE]
> Diese Methode muss aufgerufen werden, wenn Sie das [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Objekt abrufen und bevor Sie mit der Verwendung des-Objekts beginnen, wenn Sie virtuelle Eigenschaften für Symbole verwenden müssen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
