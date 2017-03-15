---
title: "SccSetOption-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccSetOption"
helpviewer_keywords: 
  - "SccSetOption-Funktion"
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccSetOption-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion legt die Optionen, die das Verhalten des Plug\-in\-Datenquellen\-Steuerelements zu steuern.  
  
## Syntax  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 nOption  
 \[in\] Die Option, die festgelegt wird.  
  
 dwVal  
 \[in\] Einstellungen für die Option.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Option wurde erfolgreich festgelegt.|  
|SCC\_I\_SHARESUBPROJOK|Zurückgegeben werden, wenn `nOption` wurde `SCC_OPT_SHARESUBPROJ` und das Quellcodeverwaltungs\-Plug\-in ermöglicht die IDE den Zielordner festgelegt.|  
|SCC\_E\_OPNOTSUPPORTED|Die Option wurde nicht festgelegt und sollte nicht zuverlässig.|  
  
## Hinweise  
 Die IDE ruft diese Funktion, um das Verhalten des Plug\-in\-Datenquellen\-Steuerelements zu steuern. Der erste Parameter, `nOption`, gibt den Wert an, die festgelegt wird, während der zweite `dwVal`, gibt an, was mit diesen Wert zu tun. Das plug\-in speichert diese Informationen zugeordnet eine `pvContext``,` daher die IDE nach dem Aufruf dieser Funktion aufrufen, muss die [SccInitialize](../extensibility/sccinitialize-function.md) \(aber nicht unbedingt nach jedem Aufruf der [SccOpenProject](../extensibility/sccopenproject-function.md)\).  
  
 Zusammenfassung der Optionen und ihre Werte:  
  
|`nOption`|`dwValue`|Beschreibung|  
|---------------|---------------|------------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Aktiviert bzw. deaktiviert Hintergrund Queuing\-Ereignis.|  
|`SCC_OPT_USERDATA`|Beliebiger Wert|Gibt einen Wert übergeben werden an Benutzer der [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Callback\-Funktion.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Gibt an, ob die IDE unterstützt derzeit einen Vorgang abbrechen.|  
|`SCC_OPT_NAMECHANGEPFN`|Zeiger auf die [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Callback\-Funktion|Ein Zeiger festgelegt auf eine Namensänderung Callback\-Funktion.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Gibt an, ob die IDE das Auschecken der Dateien manuell \(über die Benutzeroberfläche der Quelle\) oder ob sie nur über das Quellcodeverwaltungs\-Plug\-in ausgecheckt werden müssen.|  
|`SCC_OPT_SHARESUBPROJ`|Nicht zutreffend|Wenn das Quellcodeverwaltungs\-Plug\-in der IDE an den lokalen Projektordner zulässt, das plug\-in gibt `SCC_I_SHARESUBPROJOK`.|  
  
## SCC\_OPT\_EVENTQUEUE  
 Wenn `nOption` ist `SCC_OPT_EVENTQUEUE`, die IDE wird deaktiviert \(oder erneut aktivieren\) im Hintergrund. Während eine Kompilierung anweisen die IDE beispielsweise das Quellcodeverwaltungs\-Plug\-in die Verarbeitung bei Leerlauf, jeglicher Art beendet. Nach der Kompilierung würden sie Verarbeitung im Hintergrund des Plug\-ins Ereigniswarteschlange auf dem Laufenden zu bleiben erneut aktivieren. Entspricht der `SCC_OPT_EVENTQUEUE` Wert `nOption`, es gibt zwei mögliche Werte für `dwVal`, nämlich `SCC_OPT_EQ_ENABLE` und `SCC_OPT_EQ_DISABLE`.  
  
## SCC\_OPT\_HASCANCELMODE  
 Wenn der Wert für `nOption` ist `SCC_OPT_HASCANCELMODE`, die IDE ermöglicht Benutzern, lange Vorgänge abzubrechen. Festlegen von `dwVal` zu `SCC_OPT_HCM_NO` \(Standard\) gibt an, dass die IDE Modus nicht abbrechen. Das Quellcodeverwaltungs\-Plug\-in muss eine eigene Schaltfläche "Abbrechen" anbieten, wenn es die Benutzer möglicherweise abbrechen möchte.`SCC_OPT_HCM_YES` Gibt an, dass die IDE die Möglichkeit bietet, eine Operation abzubrechen, damit SCC\-Plug\-in nicht angezeigt werden eine eigene Schaltfläche "Abbrechen muss". Wenn die IDE festlegt `dwVal` zu `SCC_OPT_HCM_YES`, zur Beantwortung Vorbereitung ist `SCC_MSG_STATUS` und `DOCANCEL` Nachrichten an die `lpTextOutProc` Callback\-Funktion \(finden Sie unter [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)\). Wenn die IDE diese Variable nicht festgelegt ist, sollten das plug\-in nicht die beiden Nachrichten senden.  
  
## SCC\_OPT\_NAMECHANGEPFN  
 Wenn nOption, um festgelegt ist `SCC_OPT_NAMECHANGEPFN`, und sowohl der Quelle\-Plug\-in\-Steuerelement und die IDE ermöglichen es, das plug\-in kann tatsächlich umbenennen oder Verschieben einer Datei während eines Datenquellen\-Steuerelement. Die `dwVal` werden auf den Funktionszeiger vom Typ [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Während eines Datenquellen\-Steuerelement können das plug\-in übergeben drei Parameter dieser Funktion aufrufen. Hierbei handelt es sich um den alten Namen \(mit den vollqualifizierten Pfad\) der Datei den neuen Namen \(mit den vollqualifizierten Pfad\) der Datei, und ein Zeiger auf die Informationen, die Relevanz der IDE. Die IDE sendet in dieser letzten Zeiger durch Aufrufen von `SccSetOption` mit `nOption` festgelegt `SCC_OPT_USERDATA`, mit `dwVal` auf die Daten. Unterstützung für diese Funktion ist optional. Ein VSSCI\-Plug\-verwendet diese Fähigkeit seine Funktion Zeiger und Benutzer Datenvariablen initialisieren muss `NULL`, und es muss nicht Aufrufen einer Umbenennungsfunktion, wenn sie eine erteilt wurden. Auch vorbereitet sein sollte, den Wert enthalten soll, es wurde zugewiesen, oder als Antwort auf einen neuen Aufruf zu ändern `SccSetOption`. Dies erfolgt nicht in der Mitte einer Quelle Steuerelement Befehlsvorgang, aber es kann vorkommen, zwischen den Befehlen.  
  
## SCC\_OPT\_SCCCHECKOUTONLY  
 Wenn nOption, um festgelegt ist `SCC_OPT_SCCCHECKOUTONLY`, die IDE teilt mit, dass die Dateien im aktuell geöffneten Projekt nie manuell über das Quellcodeverwaltungssystem Benutzeroberfläche ausgecheckt werden soll. Stattdessen sollten die Dateien nur über das Quellcodeverwaltungs\-Plug\-in unter Kontrolle der IDE ausgecheckt werden. Wenn `dwValue` Wert `SCC_OPT_SCO_NO`, bedeutet, dass die Dateien normalerweise vom plug\-in behandelt werden und können, durch das Datenquellen\-Steuerelement\-Benutzeroberfläche ausgecheckt werden. Wenn `dwValue` Wert `SCC_OPT_SCO_YES`, dann nur das plug\-in kann Dateien auschecken und der Quellcode\-Verwaltungssystem UI nicht aufgerufen werden soll. Dies ist für Situationen, in denen möglicherweise die IDE "Pseudo Files", die nur über die IDE Auschecken sinnvoll.  
  
## SCC\_OPT\_SHARESUBPROJ  
 Wenn`nOption` Wert `SCC_OPT_SHARESUBPROJ`, die IDE testet, ob das Quellcodeverwaltungs\-Plug\-in einem angegebenen lokalen Ordner, beim Hinzufügen von Dateien aus Datenquellen\-Steuerelement verwenden kann. Der Wert der `dwVal` Parameter nicht in diesem Fall spielt. Lässt das plug\-in die IDE, um den lokalen Zielordner angeben, in dem die Dateien von Quelle hinzugefügt werden, steuern, wann die [SccAddFromScc](../extensibility/sccaddfromscc-function.md) aufgerufen wird, muss das plug\-in zurückgeben `SCC_I_SHARESUBPROJOK` bei der `SccSetOption` \-Funktion aufgerufen wird. Die IDE verwendet dann die `lplpFileNames` Parameter von der `SccAddFromScc` Funktion im Zielordner übergeben. Das plug\-in verwendet Zielordners, die aus Datenquellen\-Steuerelement hinzugefügt werden sollen. Wenn das plug\-in nicht liefert `SCC_I_SHARESUBPROJOK` bei der `SCC_OPT_SHARESUBPROJ` Option festgelegt ist, wird die IDE setzt voraus, dass die Plug\-in\-Dateien nur in der aktuellen lokalen Ordner hinzufügen.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)