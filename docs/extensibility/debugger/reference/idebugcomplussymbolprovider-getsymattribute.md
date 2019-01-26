---
title: IDebugComPlusSymbolProvider::GetSymAttribute | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetSymAttribute
- GetSymAttribute
ms.assetid: 6cbaac92-a60b-4165-a7f5-c34407770f3c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ec9676795fe9637bb5f361a383c17a2b0e9a15
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962835"
---
# <a name="idebugcomplussymbolprovidergetsymattribute"></a>IDebugComPlusSymbolProvider::GetSymAttribute
Ruft die Debugsymbole, mit dem angegebenen übergeordneten Attribut für das angegebene Modul ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSymAttribute (  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   _mdToken tokParent,  
   LPOLESTR pstrName,  
   ULONG32  cBuffer,  
   ULONG32* pcBuffer,  
   BYTE*    buffer  
);  
```  
  
```csharp  
int GetSymAttribute (  
   uint      ulAppDomainID,  
   Guid      guidModule,  
   int       tokParent,  
   string    pstrName,  
   uint      cBuffer,  
   out uint  pcBuffer,  
   out int[] buffer  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ulAppDomainID`  
 [in] Der Bezeichner der Anwendungsdomäne.  
  
 `guidModule`  
 [in] Eindeutiger Bezeichner des Moduls.  
  
 `tokParent`  
 [in] Token für das übergeordnete Attribut.  
  
 `pstrName`  
 [in] Der Name des Moduls.  
  
 `cBuffer`  
 [in] Anzahl der Bytes, die erforderlich sind, für die Ausgabe `buffer`.  
  
 `pcBuffer`  
 [out] Länge der Ausgabe `buffer`.  
  
 `buffer`  
 [out] Ein Array mit den Symbolen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetSymAttribute(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    _mdToken tokParent,  
    __in_z LPOLESTR pstrName,  
    ULONG32 cBuffer,  
    ULONG32 *pcBuffer,  
    BYTE buffer[])  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetSymAttribute );  
  
    IfFailGo( GetModule( idModule, &pModule) );  
  
    IfFailGo( pModule->GetSymAttribute( tokParent, pstrName, cBuffer, pcBuffer, buffer ) );  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetSymAttribute, hr);  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)