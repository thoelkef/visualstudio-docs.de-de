---
title: SccSetOption-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 282b30ff4877e76ff7e789bded57010b2ea165db
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183923"
---
# <a name="sccsetoption-function"></a>SccSetOption-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion legt die Optionen, die Steuerung des Verhaltens das Quellcodeverwaltungs-Plug-in.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 nOption  
 [in] Die Option, die festgelegt wird.  
  
 dwVal  
 [in] Einstellungen für die Option.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Option wurde erfolgreich festgelegt.|  
|SCC_I_SHARESUBPROJOK|Zurückgegeben, wenn `nOption` wurde `SCC_OPT_SHARESUBPROJ` und das Quellcodeverwaltungs-Plug-in ermöglicht die IDE, um den Zielordner festzulegen.|  
|SCC_E_OPNOTSUPPORTED|Die Option wurde nicht festgelegt und sollte nicht als zuverlässig betrachtet werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion zum Steuern des Verhaltens von das Quellcodeverwaltungs-Plug-in wird von die IDE aufgerufen. Der erste Parameter, `nOption`, gibt der Wert, der festgelegt wird, während der zweite `dwVal`, gibt an, was Sie mit diesem Wert. Das plug-in speichert diese Informationen, die zugeordnet eine `pvContext``,` daher die IDE nach dem Aufruf dieser Funktion aufrufen, muss die [SccInitialize](../extensibility/sccinitialize-function.md) (aber nicht unbedingt nach jedem Aufruf der [SccOpenProject](../extensibility/sccopenproject-function.md)).  
  
 Zusammenfassung der Optionen und ihre Werte:  
  
|`nOption`|`dwValue`|Beschreibung|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Aktiviert bzw. deaktiviert die Ereignis-queuing Hintergrundfarbe.|  
|`SCC_OPT_USERDATA`|Beliebiger Wert|Gibt einen Wert übergeben werden soll die [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Callback-Funktion.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Gibt an, ob es sich bei die IDE unterstützt derzeit einen Vorgang abgebrochen wird.|  
|`SCC_OPT_NAMECHANGEPFN`|Zeiger auf die [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Callback-Funktion|Setzt einen Zeiger auf eine Namensänderung Rückruffunktion an.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Gibt an, ob es sich bei die IDE ermöglicht die Überprüfung aus die Dateien manuell (über die Benutzeroberfläche quellcodeverwaltung), oder gibt an, ob sie nur über das Quellcodeverwaltungs-Plug-in müssen ausgecheckt sein, ein.|  
|`SCC_OPT_SHARESUBPROJ`|Nicht zutreffend|Das Quellcodeverwaltungs-Plug-in der IDE an der lokale Projektordner zulässig, das plug-in wird zurückgegeben `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Wenn `nOption` ist `SCC_OPT_EVENTQUEUE`, die IDE ist deaktiviert (oder erneutes Aktivieren) Verarbeitung im Hintergrund. Während eine Kompilierung, die IDE z. B. das Quellcodeverwaltungs-Plug-In für im Leerlauf befindlichen Verarbeitung jegliche beenden angewiesen. Nach der Kompilierung würden sie Verarbeitung im Hintergrund, das Plug-in der Ereigniswarteschlange auf dem neuesten Stand zu halten erneut aktivieren. Für die `SCC_OPT_EVENTQUEUE` Wert `nOption`, es gibt zwei mögliche Werte für `dwVal`, und zwar `SCC_OPT_EQ_ENABLE` und `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Wenn der Wert für `nOption` ist `SCC_OPT_HASCANCELMODE`, die IDE ermöglicht Benutzern, lange Vorgänge abzubrechen. Festlegen von `dwVal` zu `SCC_OPT_HCM_NO` (Standard) gibt an, dass die IDE keine Modus "Abbrechen". Das Quellcodeverwaltungs-Plug-in muss eine eigene Schaltfläche "Abbrechen" anbieten, wenn den Benutzer kann abgebrochen werden sollen. `SCC_OPT_HCM_YES` Gibt an, dass die IDE die Möglichkeit bietet, einen Vorgang abbrechen, sodass SCC-Plug-in, nicht unbedingt einen eigenen Schaltfläche "Abbrechen" angezeigt. Wenn bei die IDE `dwVal` zu `SCC_OPT_HCM_YES`, wird es auf reagieren vorbereitet `SCC_MSG_STATUS` und `DOCANCEL` Nachrichten an die `lpTextOutProc` Callback-Funktion (finden Sie unter [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Wenn diese Variable in die IDE nicht festgelegt ist, sollten das plug-in nicht diese beiden Meldungen senden.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Wenn nOption, um festgelegt ist `SCC_OPT_NAMECHANGEPFN`, und sowohl die Quelle-Plug-in-Steuerelement und die IDE ermöglichen es, das plug-in kann tatsächlich umbenennen oder Verschieben einer Datei während der einen Quellcodeverwaltungsvorgang. Die `dwVal` in einen Funktionszeiger des Typs festgelegt [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Während einen Quellcodeverwaltungsvorgang können das plug-in übergebe drei Parameter dieser Funktion aufrufen. Hierbei handelt es sich um den alten Namen (mit den vollqualifizierten Pfad) einer Datei, die den neuen Namen (mit den vollqualifizierten Pfad), der die Datei, und einen Zeiger auf die Informationen, die Relevanz der IDE. Die IDE, die in dieser letzten Zeiger durch Aufrufen von sendet `SccSetOption` mit `nOption` festgelegt `SCC_OPT_USERDATA`, mit `dwVal` verweist auf die Daten. Unterstützung für diese Funktion ist optional. Schleichwerbung VSSCI-, verwendet diese Fähigkeit der Zeiger und die Benutzer Daten die Variablen zu initialisieren, muss `NULL`, und es darf keine Rename-Funktion aufrufen, es sei denn, es einer festgelegt wurde. Es sollte auch darauf vorbereitet sein, den Wert enthalten soll, es wurde angegeben, oder So ändern Sie es als Reaktion auf einen neuen Aufruf von `SccSetOption`. Dies erfolgt nicht in der Mitte einen Befehl Quellcodeverwaltungsvorgang, aber es kann vorkommen, zwischen den Befehlen.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Wenn nOption, um festgelegt ist `SCC_OPT_SCCCHECKOUTONLY`, die IDE wird gibt an, dass die Dateien im aktuell geöffneten Projekt nie manuell über das Quellcodeverwaltungssystem Benutzeroberfläche ausgecheckt werden soll. Stattdessen sollten die Dateien nur über das Quellcodeverwaltungs-Plug-in unter Kontrolle der IDE ausgecheckt werden. Wenn `dwValue` nastaven NA hodnotu `SCC_OPT_SCO_NO`, dies bedeutet, dass die Dateien vom plug-in normalerweise behandelt werden soll, und über die Benutzeroberfläche der quellcodeverwaltung ausgecheckt werden können. Wenn `dwValue` nastaven NA hodnotu `SCC_OPT_SCO_YES`, klicken Sie dann nur das plug-in ist zulässig, checken Sie Dateien und das Quellcodeverwaltungssystem UI nicht aufgerufen werden soll. Dies ist für Situationen, in denen möglicherweise die IDE "Pseudo Files", die nur über die IDE sehen Sie sich sinnvoll.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Wenn`nOption` nastaven NA hodnotu `SCC_OPT_SHARESUBPROJ`, die IDE testet, ob das Quellcodeverwaltungs-Plug-in einem angegebenen lokalen Ordner verwenden kann, wenn Sie Dateien aus der quellcodeverwaltung hinzufügen. Der Wert des der `dwVal` Parameter spielt keine Rolle in diesem Fall. Wenn das plug-in die IDE ermöglicht, um den lokalen Zielordner anzugeben, in dem die Dateien aus der Quelle hinzugefügt werden kann werden, steuern, wann die [SccAddFromScc](../extensibility/sccaddfromscc-function.md) aufgerufen wird, und klicken Sie dann das plug-in zurückgegeben werden muss `SCC_I_SHARESUBPROJOK` bei der `SccSetOption` -Funktion ist wird aufgerufen. Anschließend verwendet die IDE die `lplpFileNames` Parameter der `SccAddFromScc` Funktion, um den Zielordner zu übergeben. Das plug-in verwendet, Zielordner, die aus der quellcodeverwaltung hinzugefügten werden soll. Wenn das plug-in nicht zurückkehrt `SCC_I_SHARESUBPROJOK` bei der `SCC_OPT_SHARESUBPROJ` Option festgelegt ist, wird die IDE wird davon ausgegangen, dass die Plug-in-Dateien nur in der aktuellen lokalen Ordner hinzufügen kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)

