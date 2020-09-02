---
title: 'Idiapropertystorage:: Read Multiple | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538082"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest angegebene Eigenschaften aus dem aktuellen Eigenschaften Satz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cpspec`  
 in Anzahl der im Array angegebenen Eigenschaften `rgpspec` . Wenn der Wert 0 (null) ist, gibt die Methode keine Eigenschaften zurück, sondern `S_OK` als Erfolgs Code zurück.  
  
 `rgpspec`  
 in Ein Array von zu lesenden Eigenschaften. Eigenschaften können entweder durch eine eigen schafts-ID oder durch einen optionalen Zeichen folgen Namen angegeben werden. Es ist nicht erforderlich, Eigenschaften in einer bestimmten Reihenfolge im Array anzugeben. Das Array kann doppelte Eigenschaften enthalten, sodass bei der Rückgabe für einfache Eigenschaften doppelte Eigenschaftswerte entstehen. Nicht einfache Eigenschaften sollten beim Versuch, Sie ein zweites Mal zu öffnen, den Zugriff verweigert zurückgeben. Das Array kann eine Mischung aus Eigenschaften-IDs und Zeichen folgen-IDs enthalten. Dieses Array muss mindestens über eine `cpspec` Anzahl von Eigenschafts Werten verfügen.  
  
 `rgvar`  
 [in, out] Ein Array von- `PROPVARIANT` Strukturen (im Microsoft. VisualStudio. OLE. Interop-Namespace), das mit Werten für jede Eigenschaft ausgefüllt werden soll. Das Array muss mindestens ein `cpspec` Element der Größe aufweisen. Der Aufrufer muss die Werte im Array nicht initialisieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn eine oder mehrere Eigenschaften nicht gefunden wurden. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Eigenschaft nicht gefunden wurde, enthält der entsprechende Eintrag im `rgvar` Array eine `VARIANT` mit dem Typ `VT_EMPTY` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
