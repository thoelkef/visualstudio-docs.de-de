---
title: "SccGet-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGet"
helpviewer_keywords: 
  - "SccGet-Funktion"
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccGet-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion ruft eine Kopie von einer oder mehreren Dateien für die Anzeige und kompilieren, aber nicht zum Bearbeiten. In den meisten Systemen werden die Dateien als schreibgeschützt gekennzeichnet.  
  
## Syntax  
  
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
  
#### Parameter  
 pvContext  
 \[in\] Der Context\-Struktur des Datenquellen\-Steuerelements\-Plug\-in.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 \[in\] Anzahl der angegebenen Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 \[in\] Array von vollständig qualifizierten Namen der Dateien abgerufen werden sollen.  
  
 Bestanden  
 \[in\] Befehl Flags \(`SCC_GET_ALL`, `SCC_GET_RECURSIVE`\).  
  
 pvOptions  
 \[in\] Quellcodeverwaltungs\-plug\-in spezifischen Optionen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Erfolg der Get\-Vorgang.|  
|SCC\_E\_FILENOTCONTROLLED|Diese Datei befindet sich nicht in Datenquellen\-Steuerelement.|  
|SCC\_E\_OPNOTSUPPORTED|Dieser Vorgang wird von Quellcode\-Verwaltungssystem nicht unterstützt.|  
|SCC\_E\_FILEISCHECKEDOUT|Die Datei, die der Benutzer derzeit ausgecheckt hat, kann nicht abgerufen werden.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NOSPECIFIEDVERSION|Eine ungültige Version oder Datum\/Uhrzeit angegeben.|  
|SCC\_E\_NONSPECIFICERROR|Unspezifischen Ausfall. Datei wurde nicht synchronisiert.|  
|SCC\_I\_OPERATIONCANCELED|Operation wurde vor dem Abschluss abgebrochen.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um diesen Vorgang auszuführen.|  
  
## Hinweise  
 Diese Funktion heißt mit einem Zähler und ein Array von Namen der Dateien abgerufen werden sollen. Wenn die IDE das Flag übergibt `SCC_GET_ALL`, dies bedeutet, dass die Elemente in `lpFileNames` sind keine Dateien jedoch Verzeichnisse, und dass alle Dateien unter Versionskontrolle in den angegebenen Verzeichnissen abgerufen werden sollen.  
  
 Die `SCC_GET_ALL` Flag kombiniert werden können, mit der `SCC_GET_RECURSIVE` Flag zum Abrufen aller Dateien in den angegebenen Verzeichnissen und auch alle Unterverzeichnisse.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` sollte nie übergeben werden, ohne `SCC_GET_ALL`. Beachten Sie, dass es sich bei Verzeichnisse C:\\A und C:\\A\\B sind beides auf einen rekursiven übergeben, C:\\A\\B und alle seine Unterverzeichnisse tatsächlich zweimal abgerufen werden. Es obliegt der IDE – und nicht die Quellcode\-Plug\-ins, um sicherzustellen, dass Duplikate wie diese aus dem Array gespeichert werden.  
  
 Abschließend angegeben werden, auch wenn ein Quellcode\-Plug\-in die `SCC_CAP_GET_NOUI` Flag bei der Initialisierung, der angibt, dass es keine Benutzeroberfläche für einen Get\-Befehl, diese Funktion kann von der IDE zum Abrufen von Dateien noch aufgerufen werden. Das Flag bedeutet lediglich, dass die IDE ein Get\-Menüelement nicht angezeigt, dass das plug\-in nicht erwartet Benutzeroberfläche bereitgestellt.  
  
## Umbenennen und SccGet  
 Problem: ein Benutzer checkt eine Datei, z. B. a.txt, und ändert. Bevor a.txt eingecheckt werden kann, ein zweiter Benutzer benennt a.txt zu "b.txt" in der Quellcode\-Verwaltungsdatenbank, checkt "b.txt", kann einige Änderungen an der Datei und checkt die Datei. Der erste Benutzer möchte die Änderungen des zweiten Benutzers der erste Benutzer wird die lokale Version der Datei "a.txt" zu "b.txt" umbenannt und Get für die Datei verfügt. Allerdings geht davon aus der lokale Cache, das verfolgt Versionsnummern weiterhin die erste Version von a.txt wird lokal gespeichert und daher Datenquellen\-Steuerelement kann nicht aufgelöst werden die Unterschiede.  
  
 Es gibt zwei Möglichkeiten, dieses Problem zu beheben, wobei der lokale Cache des Source Control\-Versionen mit Quellcode\-Verwaltungsdatenbank nicht synchronisiert wird:  
  
1.  Lassen Sie Umbenennen einer Datei im Quellcode\-Verwaltungsdatenbank, die derzeit ausgecheckt ist zu, nicht.  
  
2.  Führen Sie die Entsprechung von "Löschen alte" gefolgt von "Neu hinzufügen". Der folgende Algorithmus ist eine Möglichkeit, dies zu erreichen.  
  
    1.  Rufen Sie die [SccQueryChanges](../extensibility/sccquerychanges-function.md) Funktion erfahren Sie mehr über das Umbenennen von a.txt zu "b.txt" in der Quellcode\-Verwaltungsdatenbank.  
  
    2.  Benennen Sie die lokalen a.txt zu "b.txt".  
  
    3.  Rufen Sie die `SccGet` \-Funktion zur a.txt und "b.txt".  
  
    4.  Da a.txt in Quellcode\-Verwaltungsdatenbank nicht vorhanden ist, wird der fehlende a.txt Versionsinformationen der lokalen Cache gelöscht.  
  
    5.  Die "b.txt"\-Datei, die ausgecheckt wird, wird mit dem Inhalt der lokalen "b.txt"\-Datei zusammengeführt.  
  
    6.  Die aktualisierte "b.txt"\-Datei kann jetzt überprüft werden.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md)