---
title: IActiveScript | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a33db2bcbcb356a508fec2e6bc5449a899a1299
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577235"
---
# <a name="iactivescript"></a>IActiveScript
Stellt die Methoden bereit, die zum Initialisieren der Skript-Engine erforderlich sind. Die Skript-Engine muss die `IActiveScript`-Schnittstelle implementieren.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informiert die Skript-Engine über die [iactivescriptsite](../../winscript/reference/iactivescriptsite.md) -Website, die vom Host bereitgestellt wird.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Ruft das Site Objekt ab, das der Windows-Skript-Engine zugeordnet ist.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Versetzt die Skript-Engine in den angegebenen Zustand.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Ruft den aktuellen Zustand der Skript-Engine ab.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Bewirkt, dass die Skript-Engine alle zurzeit geladenen Skripts abschließt, den Zustand verliert und alle Schnittstellen Zeiger freigibt, die es für andere Objekte gibt, sodass ein geschlossener Zustand eintritt.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Fügt den Namen eines Elements auf Stamm Ebene dem-Namespace der Skript-Engine hinzu.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Fügt dem Namespace für das Skript eine Typbibliothek hinzu.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Ruft die `IDispatch`-Schnittstelle für das Skript ab, das ausgeführt wird.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Ruft einen von der Skript-Engine definierten Bezeichner für den aktuell ausgeführten Thread ab.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Ruft einen von der Skript-Engine definierten Bezeichner für den Thread ab, der dem angegebenen Microsoft Win32-Thread zugeordnet ist.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Ruft den aktuellen Zustand eines Skript Threads ab.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Unterbricht die Ausführung eines laufenden Skript Threads.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Klont die aktuelle Skript-Engine (abzüglich jedes aktuellen Ausführungs Zustands) und gibt eine geladene Skript-Engine zurück, die über keine Site im aktuellen Thread verfügt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)