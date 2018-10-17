---
title: SccGet-Funktion | Microsoft-Dokumentation
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
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb6f5204b1605969a37fd6528dda0ccaa7b8fe7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175200"
---
# <a name="sccget-function"></a>SccGet-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion ruft eine Kopie einer oder mehreren Dateien für das Anzeigen von und zu kompilieren, aber nicht zur Bearbeitung ab. In den meisten Systemen werden die Dateien als schreibgeschützt markiert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Die Context-Struktur, der das Quellcodeverwaltungs-Plug-in.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 nFiles  
 [in] Anzahl der angegebenen Dateien in die `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array von vollqualifizierten Namen der Dateien abgerufen werden sollen.  
  
 Bestanden  
 [in] Befehl Flags (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Erfolg des Vorgangs zum Abrufen.|  
|SCC_E_FILENOTCONTROLLED|Die Datei ist nicht unter quellcodeverwaltung.|  
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem wird dieser Vorgang nicht unterstützt.|  
|SCC_E_FILEISCHECKEDOUT|Die Datei, die der Benutzer zurzeit ausgecheckt hat, kann nicht abgerufen werden.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|SCC_E_NOSPECIFIEDVERSION|Eine ungültige Version oder Datum/Uhrzeit angegeben.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers; Datei wurde nicht synchronisiert.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang abgebrochen, vor dem Abschluss.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um diesen Vorgang auszuführen.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird mit einem Zähler und ein Array von Namen der Dateien abgerufen werden sollen, aufgerufen. Wenn die IDE das Flag übergibt `SCC_GET_ALL`, dies bedeutet, dass die Elemente in `lpFileNames` sind keine Dateien jedoch Verzeichnisse und dass alle Dateien unter quellcodeverwaltung in die angegebenen Verzeichnisse abgerufen werden sollen.  
  
 Die `SCC_GET_ALL` Flag kombiniert werden können, mit der `SCC_GET_RECURSIVE` Flag, um alle Dateien in den angegebenen Verzeichnissen und auch alle Unterverzeichnisse abzurufen.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` sollte nie übergeben werden, ohne `SCC_GET_ALL`. Beachten Sie, dass wenn Verzeichnisse C:\A und C:\A\B get in einem rekursiven übergeben sind, C:\A\B und allen seinen Unterverzeichnisse tatsächlich zweimal abgerufen werden. Es obliegt der IDE – und nicht den Quellcode-Plug-ins, um sicherzustellen, dass Duplikate, wie diese aus dem Array gespeichert werden.  
  
 Schließlich auch, wenn ein Quellcode-Plug-in angegebene die `SCC_CAP_GET_NOUI` Flag bei der Initialisierung, der angibt, dass er verfügt nicht über eine Benutzeroberfläche für einen Get-Befehl, der diese Funktion kann noch von der IDE zum Abrufen von Dateien aufgerufen werden. Das Flag bedeutet einfach, dass die IDE wird ein Get-Menüelement nicht angezeigt, dass das plug-in nicht erwartet, dass keine Benutzeroberfläche bereitstellt.  
  
## <a name="renaming-and-sccget"></a>Umbenennen und SccGet  
 Situation: ein Benutzer checkt eine Datei, z. B. "a.txt", und ändert sie. Bevor a.txt eingecheckt werden können, ein zweiter Benutzer a.txt benennt, zu "b.txt" im Quellcode-Verwaltungsdatenbank, checkt "b.txt", stellt einige Änderungen an der Datei und checkt die Datei. Der erste Benutzer möchte die Änderungen der zweite Benutzer auf der erste Benutzer wird die lokale Version der Datei "a.txt" zu "b.txt" umbenannt und Get für die Datei ist. Allerdings geht davon aus der lokale Cache, das verfolgt Versionsnummern immer noch die erste Version des a.txt lokal gespeichert, und daher Datenquellen-Steuerelement kann nicht aufgelöst werden die Unterschiede.  
  
 Es gibt zwei Möglichkeiten, dieses Problem zu beheben, in denen der lokale Cache von Source-Control-Versionen mit der Datenbank synchronisiert wird:  
  
1.  Lassen Sie Umbenennen einer Datei im Quellcode-Verwaltungsdatenbank, die derzeit ausgecheckt ist zu, nicht.  
  
2.  Führen Sie die Entsprechung von "Löschen alte" gefolgt von "Neu hinzufügen". Der folgende Algorithmus ist eine Möglichkeit, dies zu erreichen.  
  
    1.  Rufen Sie die [SccQueryChanges](../extensibility/sccquerychanges-function.md) Funktion, erfahren Sie mehr über das Umbenennen von a.txt zu "b.txt" im Quellcode-Verwaltungsdatenbank.  
  
    2.  Benennen Sie die lokalen a.txt zu "b.txt".  
  
    3.  Rufen Sie die `SccGet` -Funktion für sowohl "a.txt" und "b.txt".  
  
    4.  Da a.txt nicht im Quellcode-Verwaltungsdatenbank vorhanden ist, wird der lokalen Cache der Informationen zu fehlenden a.txt Version gelöscht.  
  
    5.  Die "b.txt"-Datei, die ausgecheckt wird, wird mit dem Inhalt der lokalen "b.txt"-Datei zusammengeführt.  
  
    6.  Die aktualisierte "b.txt"-Datei kann jetzt eingecheckt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)

