---
title: SetWefProcessId-Methode | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dd4abab178c951c6150653a1228c2077c5585808
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="setwefprocessid-method"></a>SetWefProcessId-Methode
  Enthält die Prozess-ID, die Inhalt Web Erweiterungen Framework (WEF) ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*ist dwProcessId*|Die Prozess-ID, die zum Ausführen von WEF-Inhalt verwendet werden.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode muss aufgerufen werden, nachdem der Inhalt WEF-Prozess erstellt wurde, aber bevor der Inhalt WEF ausgeführt wird.  
  
 Wenn Sie die Entwicklungsumgebung für einen Debugger an den Inhalt WEF-Prozess anfügen möchten, muss die Umgebung diesen Vorgang in der Implementierung dieser Methode ausführen.  
  
  