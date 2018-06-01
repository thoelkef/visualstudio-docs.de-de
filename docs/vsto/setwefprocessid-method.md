---
title: SetWefProcessId-Methode
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b426237816bfee53e7c3e50c19e29168b27e16e1
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693431"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId-Methode
  Enthält die Prozess-ID, die Inhalt Web Erweiterungen Framework (WEF) ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
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
  
  