---
title: IDispatchEx::InvokeEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24730080"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Ermöglicht den Zugriff auf Eigenschaften und Methoden verfügbar gemacht werden, indem ein `IDispatchEx` Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 Bezeichnet den Member. Verwendet `GetDispID` oder `GetNextDispID` die Dispatch-ID abrufen.  
  
 `lcid`  
 Der Gebietsschemakontext, in dem Argumente interpretiert werden sollen. Die `lcid` übergeben `InvokeEx` ermöglichen das Objekt, das die Argumente, die spezifisch für ein Gebietsschema interpretiert werden sollen.  
  
 `wFlags`  
 Der gültige Werte für `wFlags` sind:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Flags, die den Kontext des beschreiben die `InvokeEx` aufrufen:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|DISPATCH_METHOD|Das Element wird als eine Methode aufgerufen. Wenn eine Eigenschaft den gleichen Namen besitzt, sowohl dies als auch das DISPATCH_PROPERTYGET-Flag kann festgelegt werden (definiert durch `IDispatch`).|  
|DISPATCH_PROPERTYGET|Das Element wird als eine Eigenschaft oder einen Datenmember abgerufen (definiert durch `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Das Element wird als eine Eigenschaft oder einen Datenmember geändert (definiert durch `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Das Element wird durch einen Wert zuweisen, anstatt eine Zuweisung eines Verweises geändert. Dieses Flag gilt nur, wenn die Eigenschaft einen Verweis auf ein Objekt akzeptiert (definiert durch `IDispatch`).|  
|DISPATCH_CONSTRUCT|Das Element wird als Konstruktor verwendet. (Dies ist ein neuer Wert durch definierten `IDispatchEx`). Der gültige Werte für `wFlags` sind:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Ein Zeiger auf eine Struktur, die ein Array von Argumenten und ein Array von Argument-DISPIDs für benannte Argumente sowie Zähler für die Anzahl der Elemente in jedem Array enthält. Finden Sie unter der `IDispatch` Dokumentation für eine vollständige Beschreibung der DISPPARAMS-Struktur.  
  
 `pVarRes`  
 Zeiger auf den Speicherort, in dem das Ergebnis Null, wenn der Aufrufer kein Ergebnis erwartet oder gespeichert werden. Dieses Argument wird ignoriert, wenn DISPATCH_PROPERTYPUT oder DISPATCH_PROPERTYPUTREF angegeben wird.  
  
 `pei`  
 Ein Zeiger auf eine Struktur mit Ausnahmeinformationen. Diese Struktur ausgefüllt werden in if- `DISP_E_EXCEPTION` zurückgegeben wird. Null kann sein. Finden Sie unter der `IDispatch` Dokumentation für eine vollständige Beschreibung der `EXCEPINFO` Struktur.  
  
 `pspCaller`  
 Ein Zeiger auf ein Dienstobjekt, das vom Aufrufer, in der das Objekt, das vom Aufrufer Dienste anfordern kann. Null kann sein.  
  
 `IDispatchEx::InvokeEx`enthält alle die gleichen Funktionen wie `IDispatch::Invoke` und fügt einige Erweiterungen:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Gibt an, dass das Element als Konstruktor verwendet wird.|  
|`pspCaller`|Die `pspCaller` ermöglicht den Zugriff auf Dienste, die vom Aufrufer bereitgestellt. Bestimmte Dienste möglicherweise vom Aufrufer selbst behandelt oder an den Aufrufer weiter der Aufrufkette delegiert werden. Z. B. wenn ein Skriptmodul in ein Browser ist eine `InvokeEx` Aufruf an ein externes Objekt, das Objekt kann folgen der `pspCaller` Kette zum Abrufen von Diensten aus dem Skriptmodul oder den Browser. (Beachten Sie, dass die Aufrufkette nicht identisch mit der Erstellung-Kette ist – auch bekannt als Container Kette oder Standort-Kette. Die Erstellung Kette finden Sie möglicherweise über einen anderen Mechanismus wie z. B. `IObjectWithSite`.)|  
|`this`-Zeiger|Wenn DISPATCH_METHOD festgelegt ist, im `wFlags`, es gibt möglicherweise ein "benannter Parameter" für den Wert "this". Die DISPID DISPID_THIS werden und muss er den ersten benannten Parameter.|  
  
 Der nicht verwendeten `riid` im Parameters `IDispatch::Invoke` entfernt wurde.  
  
 Die `puArgArr` im Parameters `IDispatch::Invoke` entfernt wurde.  
  
 Finden Sie unter der `IDispatch::Invoke` Dokumentation für die folgenden Beispiele:  
  
 "Eine Methode ohne Argumente aufrufen"  
  
 "Abrufen und Festlegen von Eigenschaften"  
  
 "Übergeben von Parametern"  
  
 "Indizierte Eigenschaften"  
  
 "Durch das Auslösen von Ausnahmen während der Invoke"  
  
 "Fehler zurückgeben"  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|DISP_E_BADPARAMCOUNT|Die Anzahl der Elemente, die bereitgestellt, um DISPPARAMS unterscheidet sich von der Anzahl von Argumenten akzeptiert, indem Sie die Methode oder Eigenschaft.|  
|DISP_E_BADVARTYPE|Eines der Argumente im `rgvarg` ist kein gültiger varianter-Typ.|  
|DISP_E_EXCEPTION|Die Anwendung muss eine Ausnahme ausgelöst werden soll. In diesem Fall in übergebenen Struktur `pei` ausgefüllt werden.|  
|DISP_E_MEMBERNOTFOUND|Das angeforderte Element ist nicht vorhanden, oder der Aufruf von `InvokeEx` hat versucht, den Wert einer schreibgeschützten Eigenschaft festzulegen.|  
|DISP_E_NONAMEDARGS|Diese Implementierung der `IDispatch` unterstützt keine benannten Argumente.|  
|DISP_E_OVERFLOW|Eines der Argumente in `rgvarg` konnte nicht in den angegebenen Typ umgewandelt werden.|  
|DISP_E_PARAMNOTFOUND|Einer der Parameter DISPIDs entspricht auf einen Parameter der Methode.|  
|DISP_E_TYPEMISMATCH|Eine oder mehrere der Argumente konnte nicht umgewandelt werden.|  
|DISP_E_UNKNOWNLCID|Der aufgerufene Member interpretiert Zeichenfolgenargumente gemäß der LCID und die LCID wird nicht erkannt. Wenn der LCID nicht erforderlich ist, Argumente interpretiert werden sollen, sollte dieser Fehler nicht zurückgegeben werden.|  
|DISP_E_PARAMNOTOPTIONAL|Ein erforderlicher Parameter fehlt.|  
  
## <a name="example"></a>Beispiel  
  
```  
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
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)