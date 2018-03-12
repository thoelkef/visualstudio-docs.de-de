---
title: IActiveScriptParseProcedureOld-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld-Schnittstelle
Ermöglicht den Quelltext der Code für Prozeduren, die das Skript hinzugefügt werden. Für interpretierte Skriptsprachen, mit denen keine unabhängige erstellungsumgebung, z. B. VBScript, bietet dies eine alternative Methode (außer `IActiveScriptParse` oder `IPersist*`) den Namespace Skript Prozeduren hinzu.  
  
> [!NOTE]
>  Diese Schnittstelle ist veraltet die `IActiveScriptParseProcedure` Schnittstelle.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptParseProcedureOld` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analysiert die angegebene Prozedur aus, und fügt die Prozedur den Namespace hinzu.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)