---
title: CodeIndex-Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9586348a1862820540613a5f191132c49fa6a74d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282359"
---
# <a name="codeindex-command"></a>CodeIndex-Befehl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem **CodeIndex**-Befehl können Sie die Codeindizierung für Team Foundation Server verwalten. Beispielsweise können Sie den Index zurücksetzen, um CodeLens-Informationen zu korrigieren, oder die Indizierung deaktivieren, um Probleme mit der Serverleistung zu untersuchen.  
  
 **Erforderliche Berechtigungen**  
  
 Zum Verwenden des **CodeIndex**-Befehls müssen Sie Mitglied der Sicherheitsgruppe **Team Foundation-Administratoren** sein. Weitere Informationen finden Sie in der [Berechtigungsreferenz für Team Foundation Server](http://msdn.microsoft.com/library/39997de5-b7fb-4777-b779-07de0543abe6).  
  
> [!NOTE]
>  Sie müssen auch dann ein Fenster für die Eingabeaufforderung mit erhöhten Rechten öffnen, wenn Sie sich mit Administratoranmeldeinformationen anmelden, um diesen Befehl auszuführen. Sie müssen diesen Befehl außerdem auf der Logikschicht für Team Foundation ausführen.  
  
## <a name="syntax"></a>Syntax  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### <a name="parameters"></a>Parameter  
  
|**Argument**|**Beschreibung**|  
|------------------|---------------------|  
|`CollectionName`|Gibt den Namen der Teamprojektsammlung an. Wenn der Name Leerzeichen enthält, setzen Sie ihn in Anführungszeichen, z. B. "Fabrikam-Website".|  
|`CollectionId`|Gibt die ID der Teamprojektauflistung an.|  
|`ServerPath`|Gibt den Pfad zu einer Codedatei an.|  
  
|**Option**|**Beschreibung**|  
|----------------|---------------------|  
|**/indexingStatus**|Zeigen Sie den Status und die Konfiguration des Codeindexdiensts an.|  
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on**: Indizierung aller Changesets beginnen.<br />-   **off**: Indizierung aller Changesets beenden.<br />-   **keepupOnly**: Indizierung zuvor erstellter Changesets beenden und mit der Indizierung nur der neuen Changesets beginnen.|  
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> Sie können das Platzhalterzeichen (*) am Anfang, am Ende oder an beiden Enden des Serverpfads verwenden.|Gibt eine Liste mit Codedateien und ihren Pfaden an, die nicht indiziert werden sollen.<br /><br /> -   **add**: Die Datei, die Sie nicht indizieren möchten, zur Liste der ignorierten Dateien hinzufügen.<br />-   **remove**: Die Datei, die Sie indizieren möchten, aus der Liste der ignorierten Dateien entfernen.<br />-   **removeAll**: Die Liste der ignorierten Dateien wird geleert und die Indizierung aller Dateien begonnen.<br />-   **view**: Alle Dateien anzeigen, die nicht indiziert werden.|  
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Zeigt die angegebene Anzahl der Dateien an, die die angegebene Größe in KB überschreitet. Sie können dann mithilfe der Option **/ignoreList** diese Dateien von der Indizierung ausschließen.|  
|**/reindexAll**|Zuvor indizierte Daten werden gelöscht, und die Indizierung wird neu gestartet.|  
|**/destroyCodeIndex [/noPrompt]**|Der Codeindex wird gelöscht, und alle indizierten Daten werden entfernt. Erfordert keine Bestätigung, wenn Sie die Option **/noPrompt** verwenden.|  
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|Steuern Sie, wie viele temporäre Daten CodeLens bei der Verarbeitung von Changesets erstellt. Die Standardgrenze ist 2 GB.<br /><br /> -   **view**: Die aktuelle Größenbeschränkung anzeigen.<br />-   `SizeInGBs`: Die Größenbeschränkung ändern.<br />-   **disable**: Die Größenbeschränkung entfernen.<br /><br /> Diese Grenze wird überprüft, bevor CodeLens ein neues Changeset verarbeitet. Wenn die temporären Daten diese Grenze überschreiten, hält CodeLens die Verarbeitung vergangener und nicht neuer Changesets an. CodeLens beginnt wieder mit der Verarbeitung, nachdem die Daten bereinigt wurden und unter diese Grenze fallen. Die Bereinigung wird automatisch einmal pro Tag ausgeführt. Das bedeutet, dass temporäre Daten diese Grenze möglicherweise überschreiten, bis die Bereinigung ausgeführt wird.|  
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|Steuern, wie lange der Änderungsverlauf indiziert werden soll. Dies beeinflusst, wie viel Verlauf von CodeLens gezeigt wird. Die Standardgrenze beträgt 12 Monate. Das bedeutet, dass CodeLens Ihren Änderungsverlauf nur aus den vergangenen 12 Monaten anzeigt.<br /><br /> -   **view**: Die aktuelle Anzahl Monate anzeigen.<br />-   **all**: Gesamten Änderungsverlauf indizieren.<br />-   `NumberOfMonths`: Anzahl der Monate ändern, für die der Änderungsverlauf indiziert wird.|  
|**/collectionName:** `CollectionName`|Gibt den Namen der Teamprojektsammlung an, für die der **CodeIndex**-Befehl ausgeführt werden soll. Erforderlich, wenn Sie **/CollectionId** nicht verwenden.|  
|**/collectionId:** `CollectionId`|Gibt die ID der Teamprojektsammlung an, für die der **CodeIndex**-Befehl ausgeführt werden soll. Erforderlich, wenn Sie **/CollectionName** nicht verwenden.|  
  
## <a name="examples"></a>Beispiele  
  
> [!NOTE]
>  Die in den Beispielen genannten Unternehmen, Organisationen, Produkte, Domänennamen, E-Mail-Adressen, Logos, Personen, Orte und Ereignisse sind frei erfunden.  Jede Ähnlichkeit mit tatsächlichen Firmen, Organisationen, Produkten, Domänen, Personen, Orten, Ereignissen, E-Mail-Adressen und Logos ist rein zufällig.  
  
 So zeigen Sie den Status und die Konfiguration der Codeindizierung an:  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 So starten Sie die Indizierung aller Changesets:  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 So beenden Sie die Indizierung zuvor erstellter Changesets und starten die Indizierung nur neuer Changesets:  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 So finden Sie bis zu 50 Dateien, die größer als 10 KB sind  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 So schließen Sie eine bestimmte Datei aus der Indizierung aus und fügen Sie der Liste ignorierter Dateien hinzu:  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 So zeigen Sie alle Dateien an, die nicht indiziert werden  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 So löschen Sie zuvor indizierte Daten und starten die Indizierung neu:  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 So speichern Sie den gesamten Changeset-Verlauf:  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 So entfernen Sie die Größenbeschränkung für temporäre CodeLens-Daten und fahren mit der Indizierung unabhängig von der Größe der temporären Daten fort:  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 So löschen Sie den Codeindex mit Bestätigung:  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten der Serverkonfiguration mit TFSConfig](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62)   
 [Befehlszeilentools für TFS](http://msdn.microsoft.com/en-us/be8c997a-b97b-4e59-97f5-04db0a601a6c)



