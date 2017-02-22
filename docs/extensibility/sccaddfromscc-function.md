---
title: "SccAddFromScc-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFromScc"
helpviewer_keywords: 
  - "SccAddFromScc-Funktion"
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# SccAddFromScc-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion ermöglicht es dem Benutzer nach Dateien suchen, die bereits im Quellcode\-Verwaltungssystem und stellen anschließend die Dateien Teil des aktuellen Projekts. Diese Funktion kann z. B. eine gemeinsamen Headerdatei in das aktuelle Projekt abrufen, ohne die Datei zu kopieren. Die zurückgegebenen Array von Dateien, `lplpFileNames`, enthält die Liste der Dateien, die der Benutzer möchte die IDE\-Projekt hinzufügen.  
  
## Syntax  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpnFiles  
 \[in, out\] Ein Puffer für die Anzahl der Dateien, die in hinzugefügt werden. \(Dies ist `NULL` wenn der Arbeitsspeicher, zeigt `lplpFileNames` freigegeben werden soll. Einzelheiten finden Sie unter "Hinweise".\)  
  
 lplpFileNames  
 \[in, out\] Ein Array von Zeigern auf die Dateinamen ohne Verzeichnispfade. Dieses Array ist reserviert und freigegeben, indem das Quellcodeverwaltungs\-Plug\-in. Wenn `lpnFiles` \= 1 und `lplpFileNames` ist nicht `NULL`, der erste Name im Array auf die `lplpFileNames` den Zielordner enthält.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Dateien wurden erfolgreich gespeichert und dem Projekt hinzugefügt.|  
|SCC\_I\_OPERATIONCANCELED|Vorgang wurde mit wirkungslos abgebrochen.|  
|SCC\_I\_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
  
## Hinweise  
 Diese Funktion wird von die IDE aufgerufen. Wenn das Quellcodeverwaltungs\-Plug\-in einen lokalen Ordner angeben unterstützt, übergibt die IDE `lpnFiles` \= 1 und übergibt den Namen des lokalen Ordners in `lplpFileNames`.  
  
 Wenn der Aufruf der `SccAddFromScc` Funktion zurückgibt, das plug\-in wurde Werte zugewiesen `lpnFiles` und `lplpFileNames`, Zuordnen von Speicher für das Array des Datei\-Namen nach Bedarf \(Beachten Sie, dass diese Zuweisung den Zeiger in ersetzt `lplpFileNames`\). Das Quellcodeverwaltungs\-Plug\-in ist verantwortlich für die Platzierung aller Dateien in das Verzeichnis des Benutzers oder im Ordner angegebenen Bezeichnung. Die IDE fügt dann die Dateien auf dem IDE\-Projekt.  
  
 Schließlich die IDE ruft diese Funktion ein zweites Mal übergeben `NULL` für `lpnFiles`. Dies wird als spezielle Signal interpretiert, durch das Quellcodeverwaltungs\-Plug\-In für das Array von Dateinamen im reservierten Speicher freigeben `lplpFileNames``.`  
  
 `lplpFileNames` ist eine `char ***` Zeiger. Das Quellcodeverwaltungs\-Plug\-in wird einen Zeiger auf ein Array von Zeigern auf Dateinamen, also die Liste auf die übliche Weise für diese API übergeben.  
  
> [!NOTE]
>  Ursprüngliche Versionen der VSSCI\-API hat eine Methode an, dass das Zielprojekt für die hinzugefügten Dateien nicht bereitgestellt. Um die Semantik der entsprechend den `lplpFIleNames` Parameter wurden verbessert, um ein in\/Out\-Parameter, anstatt ein Output\-Parameter zu erleichtern. Wenn nur eine einzelne Datei angegeben wird, d. h. der Wert auf den `lpnFiles` \= 1, und klicken Sie dann auf das erste Element der `lplpFileNames` enthält den Zielordner. Verwenden Sie diese neue Semantik, die IDE\-Aufrufe der `SccSetOption` \-Funktion mit der `nOption`Parametersatz zu `SCC_OPT_SHARESUBPROJ`. Wenn ein Quellcodeverwaltungs\-Plug\-in die Semantik nicht unterstützt, gibt es `SCC_E_OPTNOTSUPPORTED`. Tun dies der Fall ist deaktiviert die Verwendung von der **Hinzufügen from Source Control** Funktion. Wenn ein plug\-in unterstützt die **Hinzufügen from Source Control** Funktion \(`SCC_CAP_ADDFROMSCC`\), muss die neue Semantik unterstützen und zurückgeben `SCC_I_SHARESUBPROJOK`.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)