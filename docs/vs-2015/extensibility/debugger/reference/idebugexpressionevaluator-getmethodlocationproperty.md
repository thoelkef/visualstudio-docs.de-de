---
title: 'Idebugexpressionevaluator:: getmethodlocationproperty | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d82b002d9253b2d48f78e74fdf964cf42d241d9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144390"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode konvertiert einen Methoden Speicherort und Offset in eine Speicheradresse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `upstrFullyQualifiedMethodPlusOffset`  
 in Der Speicherort und der Offset der Methode als Zeichenfolge.  
  
 `pSymbolProvider`  
 in Der Symbol Anbieter, ausgedrückt als [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Objekt.  
  
 `pAddress`  
 in Eine Adresse innerhalb der Methode, ausgedrückt als [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt.  
  
 `pBinder`  
 in Der als [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt ausgedrückte Binder.  
  
 `ppProperty`  
 vorgenommen Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zurück, die die Speicheradresse darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die zurückgegebene Adresse kann z. b. zum Festlegen eines Breakpoints verwendet werden.  
  
 Trotz des namens `upstrFullyQualifiedMethodPlusOffset` kann diesem Parameter ein teilweise qualifizierter Methodenname übergeben werden. In diesem Fall ist die ausgewählte Methode die Methode, die geschlossen wird `pAddress` . Die Art und Weise, wie dieser Parameter interpretiert wird, ist die Implementierung der Ausdrucks Auswertung und der unterstützten Sprache.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [Idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
