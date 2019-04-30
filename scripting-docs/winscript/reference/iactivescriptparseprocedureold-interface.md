---
title: IActiveScriptParseProcedureOld-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 520d3f1414447abfc7c018d36853b72aefbbf15f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386169"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld-Schnittstelle
Können den Code-Quelltext Verfahren für das Skript hinzugefügt werden. Für interpretierte Skriptsprachen, die nicht über eine unabhängige erstellungsumgebung, z. B. VBScript, verfügen, die Dies bietet eine alternative Methode (außer `IActiveScriptParse` oder `IPersist*`) Skript Verfahren auf den Namespace hinzufügen.  
  
> [!NOTE]
> Diese Schnittstelle ist veraltet, zugunsten des der `IActiveScriptParseProcedure` Schnittstelle.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptParseProcedureOld` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Die Prozedur angegebenen Code analysiert und fügt die Prozedur auf den Namespace.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)