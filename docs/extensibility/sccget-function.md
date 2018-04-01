---
title: SccGet Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 73f5c55b39d855eb084206ef27e2254d50377b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sccget-function"></a>SccGet-Funktion
Diese Funktion ruft eine Kopie von einer oder mehreren Dateien für das Anzeigen von und zu kompilieren, aber nicht zum Bearbeiten. In den meisten Systemen werden die Dateien als schreibgeschützt gekennzeichnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [in] Die Kontextstruktur des Datenquellen-Steuerelements-Plug-in.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 [in] Anzahl der angegebenen Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array von voll gekennzeichneten Namen der Dateien abgerufen werden sollen.  
  
 fOptions  
 [in] Befehl Flags (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Erfolg der Get-Vorgang.|  
|SCC_E_FILENOTCONTROLLED|Die Datei ist nicht in der quellcodeverwaltung.|  
|SCC_E_OPNOTSUPPORTED|Dieser Vorgang wird von das Quellcodeverwaltungssystem nicht unterstützt.|  
|SCC_E_FILEISCHECKEDOUT|Die Datei, die der Benutzer zurzeit ausgecheckt hat, kann nicht abgerufen werden.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_NOSPECIFIEDVERSION|Eine ungültige Version oder Datum/Uhrzeit angegeben.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers; Datei wurde nicht synchronisiert.|  
|SCC_I_OPERATIONCANCELED|Vorgang hat vor Abschluss abgebrochen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um diesen Vorgang auszuführen.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird mit einer Anzahl und ein Array von Namen der Dateien abgerufen werden sollen, aufgerufen. Wenn die IDE das Flag übergibt `SCC_GET_ALL`, dies bedeutet, dass die Elemente in `lpFileNames` sind keine Dateien und Verzeichnisse, und dass alle Dateien unter quellcodeverwaltung in den angegebenen Verzeichnissen abgerufen werden sollen.  
  
 Die `SCC_GET_ALL` Flag kann zusammen mit den `SCC_GET_RECURSIVE` Flag zum Abrufen aller Dateien in den angegebenen Verzeichnissen und auch alle Unterverzeichnisse.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE`sollte nie übergeben werden, ohne dass `SCC_GET_ALL`. Beachten Sie, dass es sich bei Verzeichnissen C:\A und C:\A\B sind beides auf einen rekursiven übergeben, C:\A\B und alle Unterverzeichnisse tatsächlich zweimal abgerufen werden. Es liegt in der IDE Verantwortung – und nicht die Quelle zu steuern,-Plug-ins – um sicherzustellen, dass Duplikate wie diese aus dem Array gespeichert werden.  
  
 Selbst wenn eine Quelle-Plug-in zu steuern, schließlich angegeben die `SCC_CAP_GET_NOUI` Flag bei der Initialisierung, der angibt, dass er verfügt nicht über eine Benutzeroberfläche für einen Get-Befehl, der diese Funktion kann von der IDE zum Abrufen von Dateien weiterhin aufgerufen werden. Das Flag bedeutet lediglich, dass die IDE eine Get-Menüelement nicht angezeigt und, dass das plug-in nicht wird erwartet, dass Benutzeroberfläche bereitstellen.  
  
## <a name="renaming-and-sccget"></a>Umbenennen und SccGet  
 Situation: ein Benutzer eine Datei, z. B. a.txt, überprüft und ändert sie. Bevor a.txt eingecheckt werden können, ein zweiter Benutzer benennt a.txt in b.txt um in der Quellcode-Verwaltungsdatenbank, checkt b.txt um macht einige Änderungen an der Datei und überprüft die Datei. Der erste Benutzer möchte die Änderungen, die durch den zweiten Benutzer vorgenommen werden, damit der erste Benutzer ihre lokale Version der Datei a.txt in b.txt um benennt und Get für die Datei verfügt. Allerdings geht davon aus lokale Cache, der Versionsnummern der nachverfolgt noch die erste Version des a.txt wird lokal gespeichert und daher Datenquellen-Steuerelement kann nicht aufgelöst werden die Unterschiede.  
  
 Es gibt zwei Möglichkeiten, um dieses Problem zu beheben, auf dem lokale Cache Source Control Versionen nicht synchron mit der Quellcode-Verwaltungsdatenbank wird, ein:  
  
1.  Lassen Sie Umbenennen einer Datei in der Quellcode-Verwaltungsdatenbank, die zurzeit ausgecheckt nicht zu.  
  
2.  Führen Sie das Äquivalent zu "Löschung alten" und "new hinzufügen". Der folgende Algorithmus wird eine Möglichkeit, dies zu erreichen.  
  
    1.  Rufen Sie die [SccQueryChanges](../extensibility/sccquerychanges-function.md) Funktion erfahren Sie mehr über das Umbenennen von a.txt in b.txt um in der Quellcode-Verwaltungsdatenbank.  
  
    2.  Benennen Sie die lokalen a.txt in b.txt um.  
  
    3.  Rufen Sie die `SccGet` -Funktion für a.txt und b.txt um.  
  
    4.  Da a.txt nicht in der Quellcode-Verwaltungsdatenbank vorhanden ist, wird der Cache für die lokale Version der Informationen zu fehlenden a.txt Version gelöscht.  
  
    5.  Die b.txt um Datei ausgecheckt wird, wird mit dem Inhalt der lokalen b.txt um-Datei zusammengeführt.  
  
    6.  Die aktualisierte b.txt um-Datei kann jetzt eingecheckt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)