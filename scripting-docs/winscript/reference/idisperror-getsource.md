---
title: IDispError::GetSource | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 922f95206d341773632b84c3922ea3b240d8d1ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727970"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Gibt den sprachabhängig programmgesteuerten Bezeichner für die Klasse oder eine Anwendung, die den Fehler ausgelöst.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrSource`  
 [out] Zeichenfolge, die einen programmgesteuerten Bezeichner, in das Formular enthält `progname.objectname`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, um zu bestimmen, die Klasse oder eine Anwendung, in dem die Ausnahme aufgetreten ist. Der programmatische Bezeichner kann in der Sprache, angegeben durch den Gebietsschemabezeichner (LCID), die zum Zeitpunkt des Aufrufs angegeben zurückgegeben werden.  
  
> [!NOTE]
>  Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispError-Schnittstelle](../../winscript/reference/idisperror-interface.md)