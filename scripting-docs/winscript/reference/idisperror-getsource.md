---
title: IDispError::GetSource | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a84640f020a1ff255b8c7e5dd753752e0d310a7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446882"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Gibt den sprachabhängige programmgesteuerten Bezeichner für die Klasse oder eine Anwendung, die den Fehler ausgelöst hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrSource`  
 [out] Zeichenfolge, die einen programmgesteuerten Bezeichner, in der Form enthält `progname.objectname`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, um zu bestimmen, die Klasse oder eine Anwendung, in dem die Ausnahme aufgetreten ist. Der programmatische Bezeichner kann in der Sprache, angegeben durch den Gebietsschemabezeichner (LCID), die zum Zeitpunkt des Aufrufs angegeben zurückgegeben werden.  
  
> [!NOTE]
> Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispError-Schnittstelle](../../winscript/reference/idisperror-interface.md)