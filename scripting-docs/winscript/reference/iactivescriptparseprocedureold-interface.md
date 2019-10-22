---
title: Iactivescriptparameanprocedureold-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: 4558a0cab2aea9b56db2759bb80b1287cd33ce87
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571425"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld-Schnittstelle
Ermöglicht das Hinzufügen des Quell Code Texts für Prozeduren zum Skript. Bei interpretierten Skriptsprachen, die keine unabhängige Erstellungs Umgebung haben (z. b. VBScript), stellt dies einen alternativen Mechanismus (außer `IActiveScriptParse` oder `IPersist*`) bereit, um dem Namespace Skript Prozeduren hinzuzufügen.  
  
> [!NOTE]
> Diese Schnittstelle ist zugunsten der `IActiveScriptParseProcedure`-Schnittstelle veraltet.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden, die von `IUnknown` geerbt werden, macht die `IActiveScriptParseProcedureOld`-Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analysiert die angegebene Code Prozedur und fügt die Prozedur zum Namespace hinzu.|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)