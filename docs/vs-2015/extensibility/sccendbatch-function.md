---
title: Sccendbatch-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 986056b1f5202c2fb94d27a8792ed3b0fe308944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200147"
---
# <a name="sccendbatch-function"></a>SccEndBatch-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion beendet einen Batch von Quell Code Verwaltungs Vorgängen. Diese Batches dürfen nicht eingebettet werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_OK|Der Batch der Vorgänge wurde erfolgreich abgeschlossen.|  
|SCC_E_UNKNOWNERROR|Nicht spezifischer Fehler.|  
  
## <a name="remarks"></a>Bemerkungen  
 Quell Code Verwaltungs Batches werden verwendet, um dieselben Quell Code Verwaltungsvorgänge für mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante Dialogfelder aus der Benutzer Darstellung während eines Batch Vorgangs auszuschließen. [Sccbeginbatch](../extensibility/sccbeginbatch-function.md) und die- `SccEndBatch` Funktion werden als Paar verwendet, um den Anfang und das Ende eines Vorgangs anzugeben. Sie können nicht eingefügt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
