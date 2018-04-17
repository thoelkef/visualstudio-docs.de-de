---
title: SccSetOption Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 916378ea594d14c9493535b3a28e72ea49ed4733
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccsetoption-function"></a>SccSetOption-Funktion
Diese Funktion legt Optionen, die das Verhalten des Datenquellen-Steuerelements-Plug-in zu steuern.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 nOption  
 [in] Die Option, die festgelegt wird.  
  
 dwVal  
 [in] Einstellungen für die Option.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Option wurde erfolgreich festgelegt.|  
|SCC_I_SHARESUBPROJOK|Zurückgegeben werden, wenn `nOption` wurde `SCC_OPT_SHARESUBPROJ` und die Datenquellen-Steuerelement-Plug-in kann die IDE legen Sie den Zielordner.|  
|SCC_E_OPNOTSUPPORTED|Die Option sollte wurde nicht festgelegt und nicht bei.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE Aufrufe dieser Funktion können Sie steuern das Verhalten des Datenquellen-Steuerelements-Plug-in. Der erste Parameter `nOption`, steht der Wert, der festgelegt wird, während der zweite `dwVal`, gibt an, was mit diesen Wert zu tun. Das plug-in speichert diese Informationen, die zugeordneten eine `pvContext``,` damit die IDE nach dem Aufruf dieser Funktion aufgerufen werden muss die [SccInitialize](../extensibility/sccinitialize-function.md) (jedoch nicht unbedingt nach jedem Aufruf der [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 Zusammenfassung der Optionen und ihre Werte:  
  
|`nOption`|`dwValue`|Beschreibung|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Aktiviert bzw. deaktiviert background queuing Ereignis.|  
|`SCC_OPT_USERDATA`|Beliebiger Wert|Gibt ein Benutzerwert übergeben werden die [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Rückruffunktion.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Gibt an, ob die IDE unterstützt derzeit einen Vorgang abbrechen.|  
|`SCC_OPT_NAMECHANGEPFN`|Zeiger auf die [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Callback-Funktion|Legt einen Zeiger auf eine Namensänderung Rückruffunktion fest.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Gibt an, ob die IDE zulässt, die Überprüfung aus die Dateien manuell (über die Benutzeroberfläche der Datenquellen-Steuerelement) oder gibt an, ob sie nur über die Plug-in-quellcodeverwaltung ausgecheckt werden müssen.|  
|`SCC_OPT_SHARESUBPROJ`|Nicht zutreffend|Die Datenquellen-Steuerelement-Plug-in der IDE an den lokalen Projektordner zulässig, das plug-in wird zurückgegeben `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Wenn `nOption` ist `SCC_OPT_EVENTQUEUE`, die IDE ist deaktivieren (oder erneutes Aktivieren) Verarbeitung im Hintergrund. Während eine Kompilierung weisen die IDE z. B. das Quellsteuerelement-Plug-in bei Leerlauf Verarbeitung jeglicher Art beendet. Nach der Kompilierung würden sie Verarbeitung im Hintergrund, das Plug-in der Ereigniswarteschlange auf dem neuesten Stand zu halten erneut aktivieren. Entspricht der `SCC_OPT_EVENTQUEUE` Wert `nOption`, es gibt zwei mögliche Werte für `dwVal`, nämlich `SCC_OPT_EQ_ENABLE` und `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Wenn der Wert für `nOption` ist `SCC_OPT_HASCANCELMODE`, die IDE ermöglicht Benutzern das langer Vorgänge "Abbrechen". Festlegen von `dwVal` auf `SCC_OPT_HCM_NO` (Standard) gibt an, dass die IDE keine Modus "Abbrechen" verfügt. Die Datenquellen-Steuerelement-Plug-in muss eine eigene Schaltfläche "Abbrechen" anbieten, wenn er möchte, dass den Benutzer auf "Abbrechen" können. `SCC_OPT_HCM_YES` Gibt an, dass die IDE die Möglichkeit bietet, einen Vorgang "Abbrechen" SCC-Plug-in muss sich nicht um eine eigene Schaltfläche "Abbrechen" anzeigen. Die IDE festgelegt `dwVal` auf `SCC_OPT_HCM_YES`, wird er so reagieren Sie auf vorbereitet `SCC_MSG_STATUS` und `DOCANCEL` Nachrichten an die `lpTextOutProc` Rückruffunktion (finden Sie unter [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Wenn diese Variable in die IDE nicht festgelegt ist, sollten das plug-in nicht diese beiden Meldungen senden.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Wenn nOption, um festgelegt ist `SCC_OPT_NAMECHANGEPFN`, und sowohl der Source-Plug-in-Steuerelement und die IDE ermöglichen es, das plug-in kann tatsächlich umbenennen oder Verschieben von Dateien während eines Vorgangs des Datenquellen-Steuerelement. Die `dwVal` festgelegt, um einen Funktionszeiger des Typs [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Bei einem Vorgang Source Control können das plug-in dieser Funktion können in drei Parameter übergeben aufrufen. Hierbei handelt es sich um den alten Namen (mit den vollqualifizierten Pfad) von einer Datei, die den neuen Namen (mit den vollqualifizierten Pfad) der Datei und einen Zeiger auf Informationen, die Relevanz der IDE. Die IDE sendet in dieser letzten Zeiger durch Aufrufen von `SccSetOption` mit `nOption` festgelegt `SCC_OPT_USERDATA`, mit `dwVal` verweist auf die Daten. Unterstützung für diese Funktion ist optional. Eine VSSCI-Plug-verwendet diese Fähigkeit Datenvariablen für seine Funktion Zeiger und der Benutzer zum Initialisieren muss `NULL`, und eine Rename-Funktion müssen nicht aufrufen, es sei denn, es einer festgelegt wurde. Es sollte auch vorbereitet werden, um den Wert zu speichern, es wurde angegeben, oder als Antwort auf eine neue Aufruf ändern `SccSetOption`. Dies erfolgt nicht in der Mitte einer Quelle Befehl Steuerungsvorgang, aber es kann vorkommen, zwischen den Befehlen.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Wenn nOption, um festgelegt ist `SCC_OPT_SCCCHECKOUTONLY`, die IDE ist gibt an, dass die Dateien in der aktuell geöffneten Projekt nie manuell über die Benutzeroberfläche vom Quellcodeverwaltungssystem ausgecheckt werden sollte. Stattdessen sollten die Dateien nur über die quellcodeverwaltung-Plug-in unter Kontrolle der IDE ausgecheckt werden. Wenn `dwValue` festgelegt ist, um `SCC_OPT_SCO_NO`, dies bedeutet, dass die Dateien vom plug-in normalerweise behandelt werden soll und über die Benutzeroberfläche des Datenquellen-Steuerelements ausgecheckt werden können. Wenn `dwValue` festgelegt ist, um `SCC_OPT_SCO_YES`, klicken Sie dann nur das plug-in kann beim Auschecken der Dateien und vom Quellcodeverwaltungssystem UI nicht aufgerufen werden soll. Dies ist für Situationen, in denen möglicherweise die IDE "Pseudo-Dateien", die nur über die IDE Auschecken sinnvoll.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Wenn`nOption` festgelegt ist, um `SCC_OPT_SHARESUBPROJ`, die IDE testet, ob die Datenquellen-Steuerelement-Plug-in einem angegebenen lokalen Ordner, beim Hinzufügen von Dateien aus der quellcodeverwaltung verwenden kann. Der Wert, der die `dwVal` Parameter spielt keine Rolle in diesem Fall. Wenn das plug-in die IDE auf den lokalen Zielordner anzugeben, in dem die Dateien aus der Quelle hinzugefügt werden werden, kann steuern, wann die [SccAddFromScc](../extensibility/sccaddfromscc-function.md) aufgerufen wird, muss das plug-in zurückgeben `SCC_I_SHARESUBPROJOK` beim der `SccSetOption` Funktion ist wird aufgerufen. Klicken Sie dann die IDE verwendet die `lplpFileNames` Parameter von der `SccAddFromScc` Funktion, um den Zielordner übergeben. Das plug-in verwendet diese Zielordner, platzieren die Dateien aus der quellcodeverwaltung hinzugefügt. Wenn nicht das plug-in zurückgibt `SCC_I_SHARESUBPROJOK` bei der `SCC_OPT_SHARESUBPROJ` Option festgelegt ist, wird die IDE wird davon ausgegangen, dass die Plug-in-Dateien nur in der aktuellen lokalen Ordner hinzufügen kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)