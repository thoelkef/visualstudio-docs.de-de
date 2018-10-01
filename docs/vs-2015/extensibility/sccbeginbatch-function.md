---
title: SccBeginBatch-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e62074fa30d68e4cd283fb431f0ae64cff957ed4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513555"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SccBeginBatch-Funktion](https://docs.microsoft.com/visualstudio/extensibility/sccbeginbatch-function).  
  
Diese Funktion wird eine Batch-Sequenz von Quellcodeverwaltungsvorgänge gestartet. Die [SccEndBatch](../extensibility/sccendbatch-function.md) wird aufgerufen, um den Batch beenden. Diese Batches können nicht geschachtelt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Batches von Vorgängen wurde erfolgreich gestartet.|  
|SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Source-Control-Batches werden verwendet, um die gleichen Vorgänge über mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante projektbezogene Dialogfeldern auf die Benutzeroberfläche während eines Vorgangs im Batchmodus zu vermeiden. Die `SccBeginBatch` Funktion und die [SccEndBatch](../extensibility/sccendbatch-function.md) dienen als Funktionspaar Anfang und Ende eines Vorgangs an. Sie sind nicht schachtelbar. `SccBeginBatch` Legt ein Flag, der angibt, dass ein Batchvorgang ausgeführt wird.  
  
 Während ein Batchvorgangs aktiviert ist, sollte das Quellcodeverwaltungs-Plug-in höchstens ein Dialogfeld für Fragen an den Benutzer vorhanden und die Antwort in diesem Dialogfeld auf alle nachfolgenden Operationen anwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)

