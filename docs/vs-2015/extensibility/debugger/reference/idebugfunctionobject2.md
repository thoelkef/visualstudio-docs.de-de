---
title: IDebugFunctionObject2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 972cc9af0453668e4d5393a00bb80f34e2594273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840877"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt eine Funktion dar und erweitert die [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Eine Ausdrucks Auswertung (EE) implementiert diese Schnittstelle, um eine Funktion darzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Methoden dieser Schnittstelle verzögern die von **idebugfunctionobject** auf folgende Weise:  
  
- Die **idebugevaluate** -Methode nimmt Flags an.  
  
- Die Methode " **kreateobject** " übernimmt Flags und ein Timeout.  
  
- Die Methode " **kreatestringobjectwithlength** " benötigt eine Länge.  
  
## <a name="methods"></a>Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Erstellt ein-Objekt, das einen Konstruktor mit den angegebenen Auswertungs Kennzeichen-Einstellungen und einem Timeout Wert verwendet.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Erstellt ein Zeichen folgen Objekt mit der angegebenen Länge.|  
|[Evaluieren](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Ruft die-Funktion auf und gibt den resultierenden Wert als-Objekt zurück.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
