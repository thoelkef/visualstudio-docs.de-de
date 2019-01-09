---
title: IActiveScriptAuthor::AddTypeLib | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a14a6af9c69772c150164dd9ab49cd13a6a8884
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093794"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
Der Namespace für das Skript wird eine Typbibliothek hinzugefügt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rguidTypeLib`  
 [in] Die CLSID (Klassen-ID) der Typbibliothek hinzugefügt werden.  
  
 `dwMajor`  
 [in] Die Hauptversionsnummer.  
  
 `dwMinor`  
 [in] Die Nebenversionsnummer.  
  
 `dwFlags`  
 [in] Nicht verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft `LoadTypeLib` Typbibliothek geladen. Bei erfolgreicher Ausführung diese Methode ruft `IActiveScriptAuthor::AddNamedItem` Typinformationen hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)