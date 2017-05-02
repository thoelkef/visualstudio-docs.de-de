---
title: "IDispatchEx-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispatchEx-Schnittstelle"
  - "IDispatchEx-Schnittstelle, über IDispatchEx"
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDispatchEx-Schnittstelle
`IDispatchEx`, eine Erweiterung der `IDispatch`\-Schnittstelle, Stützfunktionen entsprechend für dynamische Sprachen wie Skriptsprachen.  In diesem Abschnitt werden die `IDispatchEx`\-Schnittstelle selbst, die Unterschiede zwischen `IDispatch` und `IDispatchEx` und das Grundprinzip für die Erweiterungen.  Es wird erwartet, dass Leser mit `IDispatch` vertraut sind und Zugriff auf die `IDispatch` Dokumentation haben.  
  
## Hinweise  
 `IDispatch` wurde im Wesentlichen für Microsoft Visual Basic entwickelt.  Die primäre Einschränkung von `IDispatch` ist, dass sie ausgegangen wird, dass Objekte statisch sind.  Das heißt, da Objekte nicht während der Laufzeit ändern, können Typinformationen sie vollständig zur Kompilierzeit beschreiben.  Dynamische Ablaufmodelle, die in den Skriptsprachen wie Visual Basic Scripting Edition \(VBScript\) und [!INCLUDE[javascript](../../includes/javascript-md.md)] und Objektmodelle wie Dynamic HTML gefunden werden, eine flexiblere Schnittstelle erfordern.  
  
 `IDispatchEx` wurde entwickelt, um alle Dienste von `IDispatch` sowie von einige Erweiterungen bereitzustellen, die für dynamischere spät gebundenen Sprachen wie Skriptsprachen geeignet sind.  Die zusätzlichen Funktionen von `IDispatchEx` über die hinaus, die von `IDispatch` bereitgestellt werden, sind:  
  
-   Fügen Sie neue Member ein Objekt \("expando"\) \- verwenden `GetDispID` mit dem `fdexNameEnsure`\-Flag hinzu.  
  
-   Löschen Sie Member einer ObjektVerwendung `DeleteMemberByName` oder `DeleteMemberByDispID`.  
  
-   Groß\-\/Kleinschreibung Dispatch VorgangVerwendung `fdexNameCaseSensitive` oder `fdexNameCaseInsensitive`.  
  
-   Suche für Member mit impliziter NameVerwendung `fdexNameImplicit`.  
  
-   Listen Sie DISPID einer ObjektVerwendung `GetNextDispID` auf.  
  
-   Zuordnung von DISPID zu Element NameVerwendung `GetMemberName`.  
  
-   Abrufen von Eigenschaften Objekt MemberVerwendung `GetMemberProperties`.  
  
-   Methodenaufruf mit `this` ZeigerVerwendung `InvokeEx` mit DISPATCH\_METHOD.  
  
-   Lassen Sie Browser, die das Konzept von Namespaces unterstützen, erhält das Namespaceübergeordnetes Elemente übergeordnete Ebene einer ObjektVerwendung `GetNameSpaceParent`.  
  
 Objekte, die `IDispatchEx` unterstützen, möglicherweise auch `IDispatch` für Abwärtskompatibilität.  Die dynamische Verhalten von Objekten, die `IDispatchEx` unterstützen, hat verschiedene Auswirkungen für die `IDispatch`\-Schnittstelle dieser Objekte.  Beispielsweise nimmt `IDispatch` die folgende Annahme:  
  
-   Der Member und der Parameter DISPID müssen während der Lebensdauer des Objekts unverändert bleiben.  Dies ermöglicht einem Client, um einmal zu erhalten DISPID und sie für die spätere Verwendung zwischenzuspeichern.  
  
 Da `IDispatchEx` das Hinzufügen und Löschen von Member zulässig ist, bleibt der Satz gültigen DISPID nicht konstant.  Für `IDispatchEx`, dass die Zuordnung zwischen DISPID und Membernamen unverändert bleiben.  Das bedeutet, wenn ein Member gelöscht wird:  
  
-   Das DISPID kann nicht wiederverwendet werden, bis ein Member mit demselben Namen erstellt wurde.  
  
-   Das DISPID muss für `GetNextDispID` gültig bleiben.  
  
-   Das DISPID muss von einem `IDispatch` oder des `IDispatchEx` ordnungsgemäß akzeptiert werden, die Methode\-sie den Member erkennen muss, wie gelöscht und einen entsprechenden Fehlercode zurückgeben \(normalerweise DISP\_E\_MEMBERNOTFOUND oder S\_FALSE\).  
  
## Beispiele  
 Dieser [!INCLUDE[javascript](../../includes/javascript-md.md)] Code in der Funktion test\(\) bewirkt Folgendes:  
  
-   Erstellt ein neues Objekt, durch Aufrufen des `Object`\-Konstruktors und weist einen Zeiger auf das neue Objekt an den variablen Obj zu.  
  
-   Erstellt ein neues Element, das Elem im Objekt namens und weist der Funktionskatze zu diesem Element einen Zeiger auf.  
  
-   Ruft diese Funktion auf.  Da sie als Methode aufgerufen wird, verweist der `this` Zeiger das Objekt Obj an.  Die Funktion wird ein neues Element, Balkendiagramm, dem Objekt hinzu.  
  
 Der vollständige HTML\-Code ist:  
  
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
  
 Ein Steuerelement, das auf die gleiche Webseite platziert wurde, könnte ein Dispatchzeiger zu den Skriptmodulen vom Browser erhalten.  Das Steuerelement kann die Funktion test\(\) dann implementieren:  
  
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
  
 Code vom Steuerelement, Test, wird die gleiche Aufgabe wie die [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Funktion `test()`.  Beachten Sie, dass diese, Dispatchaufrufe in das ausgeführte [!INCLUDE[javascript](../../includes/javascript-md.md)] Modul gemacht und ändern Sie den Zustand des Moduls:  
  
-   Erhält der Dispatchzeiger zur Katzenfunktion mithilfe `GetDispID()`.  
  
-   Erhält der Dispatchzeiger zur Objektfunktion mithilfe `GetDispID()`.  
  
-   Erstellt ein Objekt, durch Aufrufen der Objektfunktion mit `InvokeEx()` und erhält ein Dispatchzeiger dem neu erstellten Objekt.  
  
-   Erstellt ein neues Element, Elem, im Objekt unter Verwendung `GetDispID()` mit dem `fdexNameEnsure`\-Flag.  
  
-   Setzt den Dispatchzeiger zur Katze in das Element unter `InvokeEx()`.  
  
-   Ruft den Dispatchzeiger zur Katze als Methode durch Aufrufen von und Übergeben `InvokeEx()` in den Dispatchzeiger zum erstellten Objekt als den `this` Zeiger an.  
  
-   Die Katzenmethode erstellt ein neues Element, Balkendiagramm, auf dem aktuellen `this`\-Objekt.  
  
-   Überprüft, ob das neue Element, Balkendiagramm, im erstellten Objekt erstellt wurde, indem Sie durch die Elemente mithilfe `GetNextDispID()` auflistete.  
  
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
  
## Methoden  
 [IDispatchEx\-Methode](../../winscript/reference/idispatchex-methods.md)