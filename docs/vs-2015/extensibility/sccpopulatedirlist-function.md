---
title: SccPopulateDirList-Funktion | Microsoft-Dokumentation
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
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 358512c94f46971cc91ef3ed065c83ba56e5ad16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511772"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SccPopulateDirList-Funktion](https://docs.microsoft.com/visualstudio/extensibility/sccpopulatedirlist-function).  
  
Diese Funktion bestimmt, welche Verzeichnisse und (optional) die Dateien, in der quellcodeverwaltung ist eine Liste der Verzeichnisse gespeichert sind, um zu überprüfen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 nDirs  
 [in] Anzahl der Verzeichnispfade, in der `lpDirPaths` Array.  
  
 lpDirPaths  
 [in] Ein Array von Verzeichnispfaden, um zu überprüfen.  
  
 pfnPopulate  
 [in] Rückruffunktion für jedes Verzeichnispfad und (optional) den Dateinamen im `lpDirPaths` (finden Sie unter [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Einzelheiten).  
  
 pvCallerData  
 [in] Wert, der unverändert an die Rückruffunktion übergeben werden soll.  
  
 Bestanden  
 [in] Eine Kombination von Werten, die steuern, wie die Verzeichnisse verarbeitet werden (finden Sie im Abschnitt "PopulateDirList Flags" [Bitflags, die von bestimmten Befehlen verwendete](../extensibility/bitflags-used-by-specific-commands.md) mögliche Werte).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Vorgang erfolgreich abgeschlossen.|  
|SCC_E_UNKNOWNERROR|Es ist ein Fehler aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Nur die Verzeichnisse und (optional) die Namen, die tatsächlich in das Quellcodeverwaltungs-Repository werden an die Rückruffunktion übergeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Fehlercodes](../extensibility/error-codes.md)

