---
title: IActiveScriptParseProcedure32 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 10cdff328216d06a3326dd3595ef8fc78bc9cfc9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348112"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Wenn die Windows-Skript-Engine die Quellcodetexts Verfahren für das Skript hinzugefügt werden kann, implementiert die `IActiveScriptParseProcedure32` Schnittstelle. Für interpretierte Skriptsprachen, die keine unabhängige erstellungsumgebung, z. B. VBScript, stellt dies einen alternativen Mechanismus (außer `IActiveScriptParse32` oder `IPersist`*) Skript-Prozeduren für den Namespace hinzufügen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Die Prozedur angegebenen Code analysiert und fügt die Prozedur auf den Namespace.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)