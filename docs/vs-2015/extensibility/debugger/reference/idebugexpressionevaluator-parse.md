---
title: Idebugexpressionevaluator::P Arse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4039534b139eeeaf20f938c6d6c358c602f96227
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155340"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode konvertiert eine Ausdrucks Zeichenfolge in einen analysierten Ausdruck.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `upstrExpression`  
 in Die Ausdrucks Zeichenfolge, die analysiert werden soll.  
  
 `dwFlags`  
 in Eine Auflistung der [Parameterflags](../../../extensibility/debugger/reference/parseflags.md) -Konstanten, die bestimmen, wie der Ausdruck analysiert werden soll.  
  
 `nRadix`  
 in Radix, das zum Interpretieren numerischer Informationen verwendet werden soll.  
  
 `pbstrError`  
 vorgenommen Gibt den Fehler als menschenlesbaren Text zurück.  
  
 `pichError`  
 vorgenommen Gibt die Zeichenposition des Starts des Fehlers in der Ausdrucks Zeichenfolge zurück.  
  
 `ppParsedExpression`  
 vorgenommen Gibt den analysierten Ausdruck in einem [idebugobjesedexpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) -Objekt zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode erzeugt einen analysierten Ausdruck, kein tatsächlicher Wert. Ein analysierte Ausdruck ist für die Auswertung bereit, d. h. in einen-Wert konvertiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugexpressionevaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [Idebugparamein dexpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
