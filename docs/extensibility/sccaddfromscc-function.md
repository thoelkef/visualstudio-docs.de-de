---
title: SccAddFromScc Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFromScc
helpviewer_keywords: SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5027e765e12ff483a9a27795990f0ddfbb479a5c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc-Funktion
Diese Funktion ermöglicht es dem Benutzer nach Dateien suchen, die bereits in das Quellcodeverwaltungssystem sind, und stellen anschließend diese Dateien Teil des aktuellen Projekts. Diese Funktion kann z. B. eine allgemeinen Headerdatei im aktuellen Projekt abrufen, ohne die Datei zu kopieren. Die zurückgegebenen Array von Dateien, `lplpFileNames`, enthält die Liste der Dateien, die der Benutzer möchte die IDE-Projekt hinzufügen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpnFiles  
 [in, out] Ein Puffer für die Anzahl der Dateien, die in hinzugefügt werden. (Dies ist `NULL` , wenn der Arbeitsspeicher auf verweist `lplpFileNames` aufgehoben werden soll. Einzelheiten finden Sie unter "Hinweise".)  
  
 lplpFileNames  
 [in, out] Ein Array von Zeigern auf die Dateinamen ohne Verzeichnispfade. Dieses Array ist reserviert und freigegeben, indem die Datenquellen-Steuerelement-Plug-in. Wenn `lpnFiles` = 1 und `lplpFileNames` nicht `NULL`, den Vornamen in das Array verweist `lplpFileNames` den Zielordner enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Dateien wurden erfolgreich gespeichert und dem Projekt hinzugefügt.|  
|SCC_I_OPERATIONCANCELED|Vorgang wurde mit wirken sich nicht abgebrochen.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE ruft diese Funktion. Wenn die Datenquellen-Steuerelement-Plug-in einen lokalen Ordner angeben unterstützt, übergibt die IDE `lpnFiles` = 1 und übergibt den Namen des lokalen Ordners in `lplpFileNames`.  
  
 Wenn der Aufruf von der `SccAddFromScc` Funktion zurückgibt, das plug-in weist Werte zugewiesen `lpnFiles` und `lplpFileNames`, belegen von Speicher für das Array des Datei-Namen nach Bedarf (Beachten Sie, dass diese Zuweisung den Zeiger im ersetzt `lplpFileNames`). Die Datenquellen-Steuerelement-Plug-in ist verantwortlich für alle Dateien platzieren, in dem Verzeichnis des Benutzers oder im Ordner "angegebenen Bezeichnung". Die IDE fügt dann die Dateien am IDE-Projekt.  
  
 Zum Schluss die IDE ruft diese Funktion ein zweites Mal übergeben `NULL` für `lpnFiles`. Dies wird als eine spezielle Signal interpretiert, von dem Datenquellen-Steuerelement-Plug-in den für das Array von Dateinamen in belegten Arbeitsspeicher freizugeben`lplpFileNames``.`  
  
 `lplpFileNames`ist eine `char ***` Zeiger. Die Datenquellen-Steuerelement-Plug-in wird einen Zeiger auf ein Array von Zeigern auf den Dateinamen, die Liste daher auf die übliche Weise übergeben, für diese API platziert.  
  
> [!NOTE]
>  Ursprüngliche Versionen der API VSSCI bot keine Möglichkeit, das Zielprojekt für die hinzugefügten Dateien anzugeben. Um dies die Semantik der Rechnung zu tragen die `lplpFIleNames` Parameter wurden verbessert, um ein in/Out-Parameter, anstatt ein Output-Parameter zu vereinfachen. Wenn nur eine einzelne Datei angegeben wird, d. h. der Wert verweist `lpnFiles` = 1, und klicken Sie dann auf das erste Element des `lplpFileNames` der Zielordner enthält. Verwenden Sie diese neue Semantik, die IDE-Aufrufe der `SccSetOption` -Funktion mit der `nOption`Parameter festgelegt wird, um `SCC_OPT_SHARESUBPROJ`. Wenn ein Quellcodeverwaltungs-Plug-in die Semantik nicht unterstützt, gibt es `SCC_E_OPTNOTSUPPORTED`. Auf diese Weise so deaktiviert der Verwendung von der **hinzufügen, aus der Quellcodeverwaltung** Funktion. Wenn eine-Plug-in unterstützt die **hinzufügen, aus der Quellcodeverwaltung** Feature (`SCC_CAP_ADDFROMSCC`), müssen sie unterstützen die neue Semantik und zurückgeben `SCC_I_SHARESUBPROJOK`.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)