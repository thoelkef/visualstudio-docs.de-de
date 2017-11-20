---
title: IDispatchEx-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a100a193f5e3abcb076fb8aaf3d64a0d0c38833
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchex-interface"></a>IDispatchEx-Schnittstelle
`IDispatchEx`, eine Erweiterung der `IDispatch` Schnittstelle unterstützt Funktionen für dynamischen Sprachen wie z. B. Skriptsprachen geeignet. In diesem Abschnitt wird beschrieben, die `IDispatchEx` Schnittstelle selbst, die Unterschiede zwischen `IDispatch` und `IDispatchEx`, und die Begründung für die Erweiterungen. Es wird erwartet, dass der Leser mit vertraut sind `IDispatch` und haben Zugriff auf die `IDispatch` Dokumentation.  
  
## <a name="remarks"></a>Hinweise  
 `IDispatch`für Microsoft Visual Basic wurde im Grunde entwickelt werden. Die primäre Einschränkung des `IDispatch` ist, es wird davon ausgegangen, dass Objekte statisch sind. Mit anderen Worten, da Objekte während der Laufzeit nicht ändern, kann Typinformationen vollständig diese zum Zeitpunkt der Kompilierung beschreiben. Dynamische-Laufzeit-Modelle, die im Skriptsprachen, z. B. Visual Basic Scripting Edition (VBScript) befinden und [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] und das Objekt modelliert, z. B. Dynamic HTML erfordern eine flexiblere Schnittstelle.  
  
 `IDispatchEx`wurde entwickelt, um alle Dienste eines bieten `IDispatch` sowie einige Erweiterungen, die für dynamischerer spät gebundenen Sprachen wie z. B. Skriptsprachen geeignet sind. Die zusätzlichen Funktionen der `IDispatchEx` jenseits von bereitgestellten `IDispatch` sind:  
  
-   Neue Elemente hinzufügen, um ein Objekt ("Expando") – verwenden Sie `GetDispID` mit der `fdexNameEnsure` Flag.  
  
-   Löschen von Elementen eines Objekts – verwenden Sie `DeleteMemberByName` oder `DeleteMemberByDispID`.  
  
-   Groß-/Kleinschreibung Dispatch-Vorgänge – verwenden Sie `fdexNameCaseSensitive` oder `fdexNameCaseInsensitive`.  
  
-   Suchen Sie nach dem Element mit dem impliziten Namen – verwenden Sie `fdexNameImplicit`.  
  
-   Auflisten von DISPIDs eines Objekts – verwenden Sie `GetNextDispID`.  
  
-   Zuordnung von DISPID zu Elementname – verwenden Sie `GetMemberName`.  
  
-   Rufen Sie die Eigenschaften des Objektmember – verwenden Sie `GetMemberProperties`.  
  
-   Der Methodenaufruf mit `this` Zeiger – verwenden Sie `InvokeEx` mit DISPATCH_METHOD.  
  
-   Zulassen von Browsern mit Unterstützung für das Konzept von Namespaces übergeordneten Speicherplatz Name eines Objekts abrufen – verwenden Sie `GetNameSpaceParent`.  
  
 -Objekte zur Unterstützung `IDispatchEx` unterstützen möglicherweise auch `IDispatch` für die Abwärtskompatibilität. Der dynamischen Natur der Objekte, die unterstützen `IDispatchEx` hat einige Auswirkungen für die `IDispatch` Schnittstelle dieser Objekte. Beispielsweise `IDispatch` geht die folgenden Annahmen aus:  
  
-   Das Element und der Parameter müssen für die Lebensdauer des Objekts DISPIDs konstant bleiben. Dadurch wird einen Client DISPIDs einmal erhalten und zur späteren Verwendung zwischenspeichern.  
  
 Da `IDispatchEx` ermöglicht das Hinzufügen und Löschen von Elementen, die den Satz von gültigen DISPIDs bleibt nicht konstant. Allerdings `IDispatchEx` erfordert, dass die Zuordnung zwischen DISPID und der Elementname gleich bleibt. Dies bedeutet, dass, wenn ein Element gelöscht wird:  
  
-   Die DISPID kann nicht wiederverwendet werden, bis ein Element mit demselben Namen erstellt wird.  
  
-   Die DISPID gültig bleiben muss `GetNextDispID`.  
  
-   Die DISPID muss ordnungsgemäß akzeptiert werden, mithilfe einer der `IDispatch` oder `IDispatchEx` Methoden – erkennen, wenn das Element gelöscht und einen entsprechende Fehlercode (in der Regel DISP_E_MEMBERNOTFOUND oder "S_FALSE") zurückgegeben werden muss.  
  
## <a name="examples"></a>Beispiele  
 Dies [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Code in der Funktion test() bewirkt Folgendes:  
  
-   Erstellt ein neues Objekt durch Aufrufen der `Object` Konstruktor und weist einen Zeiger auf das neue Objekt der Variable-Objekt  
  
-   Erstellt ein neues Element mit dem Namen Elem, in dem Objekt, und weist diesem Element einen Zeiger auf die Funktion Cat.  
  
-   Ruft diese Funktion. Da es als eine Methode aufgerufen wird, wird der `this` Zeiger verweist auf das Objekt Objekt Die Funktion fügt ein neues Element mit dem Objekt-Leiste.  
  
 Der vollständige HTML-Code ist:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Ein Steuerelement auf dieser Webseite gleichen platziert konnte einen Dispatch-Zeiger Skriptmodulen des vom Browser abgerufen werden. Das Steuerelement konnte klicken Sie dann die Funktion test() implementieren:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Code aus dem Steuerelement, zu testen, führt die gleiche Aufgabe wie die [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Funktion `test()`. Beachten Sie, dass diese Dispatch-Aufrufe in die Ausführung erfolgen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Modul und den Zustand des Moduls ändern:  
  
-   Erhält die Dispatch-Zeiger auf die Cat-Funktion mit `GetDispID()`.  
  
-   Erhält die Dispatch-Zeiger auf das Objekt mit `GetDispID()`.  
  
-   Konstruiert ein Objekt durch Aufrufen der Funktion Objekt mit `InvokeEx()` und erhält einen Dispatch-Zeiger auf das neu erstellte Objekt.  
  
-   Erstellt ein neues Element, Elem, in das Objekt mit `GetDispID()` mit der `fdexNameEnsure` Flag.  
  
-   Setzt die Dispatch-Zeiger in Katze in das Element mit `InvokeEx()`.  
  
-   Die Dispatch-Zeiger, Cat als eine Methode aufruft, durch den Aufruf `InvokeEx()` und übergeben die Dispatch-Zeiger auf das konstruierte Objekt als die `this` Zeiger.  
  
-   Die Cat-Methode erstellt ein neues Element-Leiste auf der aktuellen `this` Objekt.  
  
-   Überprüft, ob das neue Element Balken-, wurde im erstellten Objekt durch Auflisten der Elemente, die mit `GetNextDispID()`.  
  
 Der Code für das Teststeuerelement:  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Methoden  
 [IDispatchEx-Methode](../../winscript/reference/idispatchex-methods.md)