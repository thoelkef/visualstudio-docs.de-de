---
title: IDebugDocumentContext-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4c8b8639a6d4b232f82cf87fff7b069829cc46
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159452"
---
# <a name="idebugdocumentcontext-interface"></a>IDebugDocumentContext-Schnittstelle
Stellt eine abstrakte Darstellung eines Teils des Debugdokuments dar. Für Textdokumente besteht diese Darstellung eine Zeichenposition Bereich aus.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugDocumentContext` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|Gibt zurück, das Dokument, das diesem Kontext enthält.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|Listet die Codekontexte mit diesem Dokumentenkontext verknüpft ist.|