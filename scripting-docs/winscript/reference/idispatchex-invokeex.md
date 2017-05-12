---
title: "IDispatchEx::InvokeEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "InvokeEx-Methode"
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDispatchEx::InvokeEx
Stellt den Zugriff auf Eigenschaften und Methoden, die durch ein `IDispatchEx`\-Objekt verfügbar gemacht werden.  
  
## Syntax  
  
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
  
#### Parameter  
 `id`  
 Bezeichnet den Member.  Verwendung `GetDispID` oder `GetNextDispID`, in der Dispatchbezeichner.  
  
 `lcid`  
 Der Gebietsschemakontext, in dem Argumente interpretiert werden sollen.  `lcid` wird zu `InvokeEx` übergeben, um das Objekt zu ermöglichen, ihre Argumente zu interpretieren, die einem Gebietsschema bestimmt sind.  
  
 `wFlags`  
 Die gültigen Werte für `wFlags` sind:  
  
 DISPATCH\_PROPERTYGET &#124; DISPATCH\_METHOD &#124; DISPATCH\_PROPERTYPUT &#124; DISPATCH\_PROPERTYPUTREF &#124; DISPATCH\_CONSTRUCT  
  
 Flags, die den Kontext des `InvokeEx` Aufrufs beschreiben:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|DISPATCH\_METHOD|Der Member wird als Methode aufgerufen.  Wenn eine Eigenschaft denselben Namen, dies hat und das DISPATCH\_PROPERTYGET\-Flag wird festgelegt werden \(durch `IDispatch`\).|  
|DISPATCH\_PROPERTYGET|Der Member wird als Eigenschaft oder Datenmember abgerufen \(durch `IDispatch`\).|  
|DISPATCH\_PROPERTYPUT|Der Member wird als Eigenschaft oder Datenmember geändert \(durch `IDispatch`\).|  
|DISPATCH\_PROPERTYPUTREF|Der Member wird durch eine Bezugs\-Zuweisung anstelle einer Wertzuweisung geändert.  Dieses Flag ist nur gültig, wenn die Eigenschaft einen Verweis auf ein Objekt akzeptiert \(durch `IDispatch`\).|  
|DISPATCH\_CONSTRUCT|Der Member wird als Konstruktor verwendet.  \(Dies ist ein neuer Wert, der von `IDispatchEx` definiert ist\).  Die gültigen Werte für `wFlags` sind:<br /><br /> DISPATCH\_PROPERTYGET DISPATCH\_METHOD DISPATCH\_PROPERTYPUT DISPATCH\_PROPERTYPUTREF DISPATCH\_CONSTRUCT|  
  
 `pdp`  
 Ein Zeiger auf eine Struktur, die ein Array von Argumenten und ein Array von Argument\-DISPIDs für benannte Argumente sowie Zähler für die Anzahl der Elemente in jedem Array enthält.  Siehe die Dokumentation `IDispatch` für eine vollständige Beschreibung der DISPPARAMS\-Struktur.  
  
 `pVarRes`  
 Zeiger auf das Verzeichnis, in dem das Ergebnis gespeichert werden soll, oder NULL, wenn der Aufrufer kein Ergebnis erwartet.  Dieses Argument wird ignoriert, wenn DISPATCH\_PROPERTYPUT oder DISPATCH\_PROPERTYPUTREF angegeben wird.  
  
 `pei`  
 Ein Zeiger auf eine Struktur mit Ausnahmeinformationen.  Diese Struktur ausgefüllt werden soll, wenn `DISP_E_EXCEPTION` zurückgegeben wird.  Kann NULL sein.  Siehe die Dokumentation `IDispatch` für eine vollständige Beschreibung der `EXCEPINFO`\-Struktur.  
  
 `pspCaller`  
 Zeiger auf einen Dienstanbieterobjekt angegeben vom Aufrufer, der dem Objekt können, um Dienste vom Aufrufer zu erhalten.  Kann NULL sein.  
  
 `IDispatchEx::InvokeEx` stellt alle Features `IDispatch::Invoke` bereit und werden mehrere Erweiterungen hinzu:  
  
|||  
|-|-|  
|DISPATCH\_CONSTRUCT|Gibt an, dass das Element als Konstruktor verwendet wird.|  
|`pspCaller`|`pspCaller` ermöglicht den Zugriff auf die Dienste, die vom Aufrufer bereitgestellt werden.  Bestimmte Dienste werden vom Aufrufer selbst behandelt oder für Aufrufer weiter in der Aufrufkette delegiert werden.  Wenn beispielsweise ein Skriptmodul in einem Browser einen `InvokeEx` Aufruf eines externen Objekt ausführt, kann das Objekt der `pspCaller` Kette ausführen, um Dienste vom Skriptmodul oder vom Browser zu erhalten.  \(Beachten Sie, dass die Aufrufkette nicht mit der Erstellung Kette\-auch ist, die als Containerkette oder Sitekette bezeichnet wird.  Die Erstellungskette kann durch anderen Mechanismus wie `IObjectWithSite` verfügbar.\)|  
|`this` Zeiger|Wenn DISPATCH\_METHOD in `wFlags` festgelegt ist, kann jedoch einen "benannten Parameter" für den "diesen Wert".  Das DISPID ist DISPID\_THIS und muss der erste benannte Parameter sein.|  
  
 Der nicht verwendete `riid`\-Parameter in `IDispatch::Invoke` wurde entfernt.  
  
 Der `puArgArr`\-Parameter in `IDispatch::Invoke` wurde entfernt.  
  
 Siehe die `IDispatch::Invoke` Dokumentation für die folgenden Beispiele:  
  
 Eine Methode "ohne Argumente Aufruf"  
  
 Abrufen und Festlegen "Eigenschaften"  
  
 "Parameter mit"  
  
 Indizierte Eigenschaften" "  
  
 "Ausnahmen während des Aufrufs für"  
  
 "Fehler" zurückgeben  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|||  
|-|-|  
|`S_OK`|Erfolgreich.|  
|DISP\_E\_BADPARAMCOUNT|Die Anzahl der Elemente, die in DISPPARAMS bereitgestellt werden, entspricht der Anzahl von Argumenten unterscheiden, die durch die Methode oder Eigenschaft akzeptiert werden.|  
|DISP\_E\_BADVARTYPE|Eines der Argumente in `rgvarg` ist kein gültiger varianter Typ.|  
|DISP\_E\_EXCEPTION|Die Anwendung muss eine Ausnahme auslösen.  In diesem Fall sollte die Struktur, die in `pei` übergeben wird, gefüllt werden.|  
|DISP\_E\_MEMBERNOTFOUND|Der angeforderte Member ist nicht vorhanden, oder der Aufruf `InvokeEx` versucht, den Wert einer schreibgeschützten Eigenschaft festzulegen.|  
|DISP\_E\_NONAMEDARGS|Diese Implementierung von `IDispatch` unterstützt keine benannte Argumente.|  
|DISP\_E\_OVERFLOW|Eines der Argumente in `rgvarg` konnte nicht in den angegebenen Typ umgewandelt werden.|  
|DISP\_E\_PARAMNOTFOUND|Ein des Parameters DISPID entspricht nicht auf einen Parameter in der Methode.|  
|DISP\_E\_TYPEMISMATCH|Eine oder mehrere der Argumente konnten nicht umgewandelt werden.|  
|DISP\_E\_UNKNOWNLCID|Der Member, der aufgerufen wird, interpretiert Zeichenfolgenargumente entsprechend der LCID, und die LCID wird nicht erkannt.  Wenn die LCID nicht erforderlich ist, um Argumente zu interpretieren, sollte dieser Fehler nicht zurückgegeben werden.|  
|DISP\_E\_PARAMNOTOPTIONAL|Ein erforderlicher Parameter wurde ausgelassen.|  
  
## Beispiel  
  
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
  
## Siehe auch  
 [IDispatchEx\-Schnittstelle](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)