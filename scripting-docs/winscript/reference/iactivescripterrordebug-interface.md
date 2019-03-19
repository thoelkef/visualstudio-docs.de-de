---
title: IActiveScriptErrorDebug-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 936770859d3bdfe81c84245d32ae63346b142a01
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153746"
---
# <a name="iactivescripterrordebug-interface"></a>IActiveScriptErrorDebug-Schnittstelle
Stellt den Dokument-Kontextinformationen für Kompilierungsfehler und Laufzeitausnahmen bereit. Die `IActiveScriptError::QueryInterface` -Methode unterstützt die `IActiveScriptErrorDebug` Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IActiveScriptError`, `IActiveScriptErrorDebug` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Der Dokumentenkontext bereitgestellt für diesen Fehler.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Stellt den Stapelrahmen, der für Laufzeitfehler gültig ist.|