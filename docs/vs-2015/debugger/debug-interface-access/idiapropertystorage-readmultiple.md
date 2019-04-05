---
title: IDiaPropertyStorage::ReadMultiple | Microsoft-Dokumentation
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957274"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Liest die angegebenen Eigenschaften aus der aktuellen Gruppe der Eigenschaft.  
  
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
 [in] Die Anzahl der in der angegebenen Eigenschaften der `rgpspec` Array. Falls der Wert NULL ist, wird die Methode gibt keine Eigenschaften zurück, aber gibt zurück, `S_OK` als einen Erfolgscode.  
  
 `rgpspec`  
 [in] Ein Array von Eigenschaften, die gelesen werden. Eigenschaften können entweder durch eine Eigenschafts-ID oder durch eine optionale Zeichenfolgenname angegeben werden. Es ist nicht erforderlich, um Eigenschaften in einer bestimmten Reihenfolge im Array anzugeben. Das Array kann doppelte Eigenschaften, was zu doppelten Eigenschaftswerten bei der Rückgabe für einfache Eigenschaften enthalten. Nicht-Simple-Eigenschaften sollten Zurückgeben der Zugriff verweigert beim Versuch, die sie ein zweites Mal zu öffnen. Das Array kann eine Mischung von Eigenschaft-IDs und Zeichenfolgen-IDs enthalten. Dieses Array benötigen mindestens `cpspec` Anzahl von Eigenschaftswerten.  
  
 `rgvar`  
 [in, out] Ein Array von `PROPVARIANT` Strukturen (im Namespace Microsoft.VisualStudio.OLE.Interop) mit Werten für jede Eigenschaft gefüllt werden soll. Das Array muss mindestens `cpspec` Elemente in der Größe. Der Aufrufer muss es sich nicht um die Werte im Array zu initialisieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn mindestens eine der Eigenschaften wurde nicht gefunden. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Eigenschaft wurde nicht gefunden, den zugehörigen Eintrag in der `rgvar` Array enthält einen `VARIANT` mit dem Typ des `VT_EMPTY`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
