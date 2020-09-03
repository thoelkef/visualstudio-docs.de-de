---
title: Sccbeginbatch-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 264d9057bf4f17281d6d8a16ed3a6794004e0e21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189560"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion startet eine Batch Sequenz von Quell Code Verwaltungs Vorgängen. [Sccendbatch](../extensibility/sccendbatch-function.md) wird aufgerufen, um den Batch zu beenden. Diese Batches dürfen nicht eingebettet werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_OK|Der Batch von Vorgängen wurde erfolgreich gestartet.|  
|SCC_E_UNKNOWNERROR|Nicht spezifischer Fehler.|  
  
## <a name="remarks"></a>Bemerkungen  
 Quell Code Verwaltungs Batches werden verwendet, um dieselben Vorgänge für mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante pro-Projekt-Dialogfelder aus der Benutzer Darstellung während eines Batch Vorgangs auszuschließen. Die `SccBeginBatch` -Funktion und [sccendbatch](../extensibility/sccendbatch-function.md) werden als Funktions paar verwendet, um den Anfang und das Ende eines Vorgangs anzugeben. Sie können nicht eingefügt werden. `SccBeginBatch` legt ein Flag fest, das angibt, dass ein Batch Vorgang ausgeführt wird.  
  
 Während ein Batch Vorgang wirksam ist, sollte das Quellcodeverwaltungs-Plug-in höchstens ein Dialogfeld für jede Frage für den Benutzer vorhanden sein und die Antwort von diesem Dialogfeld auf alle nachfolgenden Vorgänge anwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
