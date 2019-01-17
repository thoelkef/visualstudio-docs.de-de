---
title: IActiveScriptParseProcedureOld-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa7ea909680afdb65004f47e458d735e82ead929
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349990"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld-Schnittstelle
Können den Code-Quelltext Verfahren für das Skript hinzugefügt werden. Für interpretierte Skriptsprachen, die nicht über eine unabhängige erstellungsumgebung, z. B. VBScript, verfügen, die Dies bietet eine alternative Methode (außer `IActiveScriptParse` oder `IPersist*`) Skript Verfahren auf den Namespace hinzufügen.  
  
> [!NOTE]
>  Diese Schnittstelle ist veraltet, zugunsten des der `IActiveScriptParseProcedure` Schnittstelle.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptParseProcedureOld` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Die Prozedur angegebenen Code analysiert und fügt die Prozedur auf den Namespace.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)