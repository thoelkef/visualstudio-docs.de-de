---
title: SetWefProcessId-Methode
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7807d0495c5f0548178b1bc2ecae12d57cc3b072
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876121"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId-Methode
  Enthält die Prozess-ID, die Inhalte der Web-Extensions-Framework (WEF) ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*dwProcessId*|Die Prozess-ID, die zum Ausführen von Windows-Ereignisweiterleitung Inhalt verwendet werden.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode muss aufgerufen werden, nachdem der Inhalt WEF-Prozess erstellt wurde, aber bevor Inhalte WEF ausgeführt wird.  
  
 Wenn Sie die Entwicklungsumgebung einen Debugger an den Windows-Ereignisweiterleitung Content-Prozess anfügen möchten, muss die Umgebung diesen Vorgang in der Implementierung dieser Methode ausführen.  
