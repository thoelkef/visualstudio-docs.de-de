---
title: 'IDispatchEx:: invokeex | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 673b3f1e64caa79dc2b21641209423d93fe0f834
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144414"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Bietet Zugriff auf Eigenschaften und Methoden, die von einem-Objekt verfügbar gemacht werden `IDispatchEx` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 Bezeichnet den Member. Verwendet `GetDispID` oder `GetNextDispID` , um den Dispatchbezeichner abzurufen.  
  
 `lcid`  
 Der Gebietsschemakontext, in dem Argumente interpretiert werden sollen. `lcid`Wird an das-Objekt übermittelt, `InvokeEx` damit das-Objekt die für ein Gebiets Schema spezifischen Argumente interpretieren kann.  
  
 `wFlags`  
 Die zulässigen Werte für lauten `wFlags` :  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Flags, die den Kontext des `InvokeEx` Aufrufes beschreiben:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|DISPATCH_METHOD|Der Member wird als-Methode aufgerufen. Wenn eine Eigenschaft denselben Namen hat, können sowohl dieses als auch das DISPATCH_PROPERTYGET-Flag festgelegt werden (definiert durch `IDispatch` ).|  
|DISPATCH_PROPERTYGET|Der Member wird als Eigenschaft oder Datenmember abgerufen (definiert durch `IDispatch` ).|  
|DISPATCH_PROPERTYPUT|Der Member wird als Eigenschaft oder Datenmember (definiert durch) geändert `IDispatch` .|  
|DISPATCH_PROPERTYPUTREF|Der Member wird durch eine Verweis Zuweisung und nicht durch eine Wert Zuweisung geändert. Dieses Flag ist nur gültig, wenn die-Eigenschaft einen Verweis auf ein Objekt akzeptiert (definiert durch `IDispatch` ).|  
|DISPATCH_CONSTRUCT|Der Member wird als Konstruktor verwendet. (Dies ist ein neuer Wert, der von definiert wird `IDispatchEx` .) Die zulässigen Werte für lauten `wFlags` :<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Ein Zeiger auf eine Struktur, die ein Array von Argumenten und ein Array von Argument-DISPIDs für benannte Argumente sowie Zähler für die Anzahl der Elemente in jedem Array enthält. `IDispatch`Eine vollständige Beschreibung der dispparameams-Struktur finden Sie in der Dokumentation.  
  
 `pVarRes`  
 Ein Zeiger auf den Speicherort, an dem das Ergebnis gespeichert werden soll, oder NULL, wenn der Aufrufer kein Ergebnis erwartet. Dieses Argument wird ignoriert, wenn DISPATCH_PROPERTYPUT oder DISPATCH_PROPERTYPUTREF angegeben wird.  
  
 `pei`  
 Ein Zeiger auf eine Struktur mit Ausnahmeinformationen. Diese Struktur sollte ausgefüllt werden, wenn `DISP_E_EXCEPTION` zurückgegeben wird. Kann NULL sein. `IDispatch`Eine vollständige Beschreibung der Struktur finden Sie in der Dokumentation `EXCEPINFO` .  
  
 `pspCaller`  
 Zeiger auf ein vom Aufrufer bereitgestelltes Dienstanbieter Objekt, das dem Objekt das Abrufen von Diensten vom Aufrufer ermöglicht. Kann NULL sein.  
  
 `IDispatchEx::InvokeEx`bietet die gleichen Features wie `IDispatch::Invoke` und fügt einige Erweiterungen hinzu:  
  
|Wert|Bedeutung|
|-|-|  
|DISPATCH_CONSTRUCT|Gibt an, dass das Element als Konstruktor verwendet wird.|  
|`pspCaller`|`pspCaller`Ermöglicht dem-Objekt den Zugriff auf Dienste, die vom Aufrufer bereitgestellt werden. Bestimmte Dienste können vom Aufrufer selbst verarbeitet oder an Aufrufer weiter oben in der Aufruf Kette delegiert werden. Wenn eine Skript-Engine in einem Browser beispielsweise einen-Befehl `InvokeEx` an ein externes Objekt sendet, kann das Objekt der `pspCaller` Kette folgen, um Dienste von der Skript-Engine oder vom Browser abzurufen. (Beachten Sie, dass die-Rückruf Kette nicht mit der Erstellungs Kette identisch ist – auch als Container Kette oder Site Kette bezeichnet. Die Erstellungs Kette ist möglicherweise über einen anderen Mechanismus verfügbar, z `IObjectWithSite` . b..)|  
|`this`-Zeiger|Wenn DISPATCH_METHOD in festgelegt ist `wFlags` , kann für den Wert "This" ein "benannter Parameter" vorhanden sein. Die DISPID wird DISPID_THIS und muss der erste benannte Parameter sein.|  
  
 Der nicht verwendete `riid` Parameter in wurde `IDispatch::Invoke` entfernt.  
  
 Der- `puArgArr` Parameter in wurde `IDispatch::Invoke` entfernt.  
  
 Die folgenden Beispiele finden Sie in der `IDispatch::Invoke` Dokumentation:  
  
 "Aufrufen einer Methode ohne Argumente"  
  
 "Eigenschaften erhalten und festlegen"  
  
 Übergeben von Parametern  
  
 "Indizierte Eigenschaften"  
  
 "Auslösen von Ausnahmen während des Aufrufs"  
  
 "Rückgabe von Fehlern"  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Wert|Bedeutung|  
|-|-|  
|`S_OK`|Erfolg.|  
|DISP_E_BADPARAMCOUNT|Die Anzahl der Elemente, die für DISPPARAMS bereitgestellt werden, unterscheidet sich von der Anzahl der von der Methode oder der Eigenschaft akzeptierten Argumente.|  
|DISP_E_BADVARTYPE|Eines der Argumente in `rgvarg` ist kein gültiger VARIANT-Typ.|  
|DISP_E_EXCEPTION|Die Anwendung muss eine Ausnahme auslöst. In diesem Fall sollte die Struktur, die in der-Struktur übermittelt `pei` wird, ausgefüllt werden.|  
|DISP_E_MEMBERNOTFOUND|Das angeforderte Element ist nicht vorhanden, oder der `InvokeEx` Versuch, den Wert einer schreibgeschützten Eigenschaft festzulegen, ist nicht vorhanden.|  
|DISP_E_NONAMEDARGS|Diese Implementierung von `IDispatch` unterstützt keine benannten Argumente.|  
|DISP_E_OVERFLOW|Eines der Argumente in `rgvarg` konnte nicht in den angegebenen Typ umgewandelt werden.|  
|DISP_E_PARAMNOTFOUND|Einer der Parameter DispIds entspricht keinem Parameter in der Methode.|  
|DISP_E_TYPEMISMATCH|Mindestens eines der Argumente konnte nicht erzwungen werden.|  
|DISP_E_UNKNOWNLCID|Der Member, der aufgerufen wird, interpretiert Zeichen folgen Argumente gemäß der LCID, und die LCID wird nicht erkannt. Wenn die LCID nicht erforderlich ist, um Argumente zu interpretieren, sollte dieser Fehler nicht zurückgegeben werden.|  
|DISP_E_PARAMNOTOPTIONAL|Ein erforderlicher Parameter wurde ausgelassen.|  
  
## <a name="example"></a>Beispiel  
  
```cpp
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)