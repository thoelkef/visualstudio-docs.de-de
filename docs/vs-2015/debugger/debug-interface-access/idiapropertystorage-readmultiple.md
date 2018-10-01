---
title: IDiaPropertyStorage::ReadMultiple | Microsoft-Dokumentation
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
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7acd4d11167adfc086aa462f51324a80a79e0e4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515191"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDiaPropertyStorage::ReadMultiple](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiapropertystorage-readmultiple).  
  
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
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn mindestens eine der Eigenschaften wurde nicht gefunden. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Eigenschaft wurde nicht gefunden, den zugehörigen Eintrag in der `rgvar` Array enthält einen `VARIANT` mit dem Typ des `VT_EMPTY`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)



