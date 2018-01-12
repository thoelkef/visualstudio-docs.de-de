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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5c27588eb6d09c0565b4b4d8faec52239ef792f7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
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
  
  