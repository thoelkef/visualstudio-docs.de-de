---
title: IDebugHelper-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f0f70ecb8ead264d0d4b074f8fc1d9e3a6091eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727310"
---
# <a name="idebughelper-interface"></a>IDebugHelper-Schnittstelle
Dient als Factory für Objektkatalogen und einfache Verbindung verweist. Der Prozess-Manager (PDM) implementiert diese Schnittstelle, die von Script-Module genutzt wird.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugHelper` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Gibt einen Eigenschaftenbrowser, der dient als Wrapper für eine Variante zurück.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Gibt einen Eigenschaftenbrowser, der eine Variante umschließt und kann für die benutzerdefinierte Konvertierung von VARIANT-Werten oder VARTYPE-Typen in Zeichenfolgen zurück.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Gibt eine Ereignisschnittstelle, die dient als Wrapper für einen bestimmten `IDispatch` Objekt.|