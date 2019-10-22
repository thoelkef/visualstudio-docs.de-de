---
title: Iactivescriptparser | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c20947a125766547565d99c5762c20e23652da1a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561669"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Wenn die Windows Script-Engine zulässt, dass dem Skript der Quellcode Text für Prozeduren hinzugefügt wird, wird die `IActiveScriptParseProcedure`-Schnittstelle implementiert. Bei interpretierten Skriptsprachen, die keine unabhängige Erstellungs Umgebung haben (z. b. VBScript), bietet dies einen alternativen Mechanismus (außer `IActiveScriptParse` oder `IPersist` *), um dem Namespace Skript Prozeduren hinzuzufügen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analysiert die angegebene Code Prozedur und fügt die Prozedur zum-Namespace hinzu.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)