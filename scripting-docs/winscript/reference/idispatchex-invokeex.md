---
title: IDispatchEx::InvokeEx | Microsoft-Dokumentation
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
ms.openlocfilehash: e631ecca1181a25fa3cf419f5fc96666f0db3cd6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086527"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Ermöglicht den Zugriff auf Eigenschaften und Methoden verfügbar gemacht werden, indem ein `IDispatchEx` Objekt.  
  
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
 Bezeichnet den Member. Verwendet `GetDispID` oder `GetNextDispID` die Dispatch-ID abgerufen.  
  
 `lcid`  
 Der Gebietsschemakontext, in dem Argumente interpretiert werden sollen. Die `lcid` übergeben wird, um `InvokeEx` können das Objekt, das die Argumente, die spezifisch für ein Gebietsschema zu interpretieren.  
  
 `wFlags`  
 Die gültige Werte für `wFlags` sind:  
  
 DISPATCH_PROPERTYGET &AMP;#124; DISPATCH_METHOD &AMP;#124; DISPATCH_PROPERTYPUT &AMP;#124; DISPATCH_PROPERTYPUTREF &AMP;#124; DISPATCH_CONSTRUCT  
  
 Flags, die den Kontext der beschreiben die `InvokeEx` aufrufen:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|DISPATCH_METHOD|Das Element wird als eine Methode aufgerufen. Wenn eine Eigenschaft auf den gleichen Namen aufweist, sowohl dies als auch das DISPATCH_PROPERTYGET-Flag kann festgelegt werden (definiert durch `IDispatch`).|  
|DISPATCH_PROPERTYGET|Das Element wird als eine Eigenschaft oder Datenmember abgerufen (definiert durch `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Das Element als eine Eigenschaft oder Datenmember geändert wird (definiert durch `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Das Element wird durch eine Zuweisung eines Verweises und nicht als einer wertzuweisung geändert. Dieses Flag gilt nur, wenn die Eigenschaft einen Verweis auf ein Objekt akzeptiert (definiert durch `IDispatch`).|  
|DISPATCH_CONSTRUCT|Das Element wird als Konstruktor verwendet. (Dies ist ein neuer Wert durch definiert `IDispatchEx`). Die gültige Werte für `wFlags` sind:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Ein Zeiger auf eine Struktur, die ein Array von Argumenten und ein Array von Argument-DISPIDs für benannte Argumente sowie Zähler für die Anzahl der Elemente in jedem Array enthält. Finden Sie unter den `IDispatch` Dokumentation für eine vollständige Beschreibung der DISPPARAMS-Struktur.  
  
 `pVarRes`  
 Zeiger auf den Speicherort, in dem das Ergebnis ist, werden gespeicherte oder Null, wenn der Aufrufer kein Ergebnis erwartet. Dieses Argument wird ignoriert, wenn DISPATCH_PROPERTYPUT oder DISPATCH_PROPERTYPUTREF angegeben wird.  
  
 `pei`  
 Ein Zeiger auf eine Struktur mit Ausnahmeinformationen. Diese Struktur eingetragen werden soll, in Wenn `DISP_E_EXCEPTION` zurückgegeben wird. Null kann sein. Finden Sie unter den `IDispatch` Dokumentation für eine vollständige Beschreibung der `EXCEPINFO` Struktur.  
  
 `pspCaller`  
 Zeiger auf ein Dienstanbieterobjekt, angegeben durch den Aufrufer, der das Objekt, das vom Aufrufer Dienste anfordern kann. Null kann sein.  
  
 `IDispatchEx::InvokeEx` enthält alle die gleichen Features wie `IDispatch::Invoke` und fügt einige Erweiterungen:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Gibt an, dass das Element als Konstruktor verwendet wird.|  
|`pspCaller`|Die `pspCaller` ermöglicht den Zugriff auf Dienste, die vom Aufrufer bereitgestellt wird. Bestimmte Dienste möglicherweise vom Aufrufer selbst behandelt oder an den Aufrufer weiter am oberen Ende der Aufrufkette delegiert werden. Z. B. wenn eine Skript-Engine in ein Browser ist eine `InvokeEx` Aufruf an ein externes Objekt, das Objekt kann folgen der `pspCaller` Kette zum Abrufen von Diensten über die Skript-Engine oder den Browser. (Beachten Sie, dass die Aufrufkette nicht identisch mit der Erstellung-Kette ist – auch bekannt als Container Kette oder Standort-Kette. Die Kette erstellen möglicherweise über einen anderen Mechanismus zur Verfügung wie z. B. `IObjectWithSite`.)|  
|`this`-Zeiger|Wenn DISPATCH_METHOD festgelegt ist, im `wFlags`, es gibt möglicherweise ein "benannte Parameter" für den Wert "this". Die DISPID DISPID_THIS werden und muss der erste benannte Parameter.|  
  
 Der nicht verwendeten `riid` Parameter im `IDispatch::Invoke` wurde entfernt.  
  
 Die `puArgArr` Parameter im `IDispatch::Invoke` wurde entfernt.  
  
 Finden Sie unter den `IDispatch::Invoke` Dokumentation für die folgenden Beispiele:  
  
 "Eine Methode ohne Argumente aufrufen"  
  
 "Abrufen und Festlegen von Eigenschaften"  
  
 "Übergeben von Parametern"  
  
 "Indizierte Eigenschaften"  
  
 "Auslösen von Ausnahmen während der Invoke"  
  
 "Fehler zurückgeben"  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|DISP_E_BADPARAMCOUNT|Die Anzahl der Elemente, die bereitgestellt, um DISPPARAMS unterscheidet sich von der Anzahl der Argumente, die von der Methode oder Eigenschaft akzeptiert.|  
|DISP_E_BADVARTYPE|Eines der Argumente in `rgvarg` ist kein gültiger varianter Typ.|  
|DISP_E_EXCEPTION|Die Anwendung muss sich um eine Ausnahme auszulösen. In diesem Fall die Zeitstruktur `pei` eingetragen werden soll.|  
|DISP_E_MEMBERNOTFOUND|Der angeforderte Member nicht vorhanden, oder der Aufruf `InvokeEx` hat versucht, den Wert einer schreibgeschützten Eigenschaft festzulegen.|  
|DISP_E_NONAMEDARGS|Diese Implementierung der `IDispatch` unterstützt keine benannten Argumente.|  
|DISP_E_OVERFLOW|Eines der Argumente in `rgvarg` konnte nicht in den angegebenen Typ umgewandelt werden.|  
|DISP_E_PARAMNOTFOUND|Einer der Parameter DISPIDs entspricht jedoch nicht auf einen Parameter für die Methode.|  
|DISP_E_TYPEMISMATCH|Eine oder mehrere der Argumente können nicht umgewandelt werden.|  
|DISP_E_UNKNOWNLCID|Die aufgerufenen Member interpretiert, Zeichenfolgenargumente entsprechend dem LCID, und die LCID wird nicht erkannt. Wenn die LCID nicht erforderlich ist, um Argumente zu interpretieren, sollte dieser Fehler nicht zurückgegeben werden.|  
|DISP_E_PARAMNOTOPTIONAL|Es wurde ein erforderlicher Parameter weggelassen.|  
  
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
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)