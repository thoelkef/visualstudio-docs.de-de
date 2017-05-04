---
title: "Registrierungseintr&#228;ge f&#252;r VSTO-Add-Ins | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "LoadBehavior-Eintrag"
  - "Add-Ins [Office-Entwicklung in Visual Studio], Registrierungseinträge"
  - "Registrierungsschlüssel [Office-Entwicklung in Visual Studio]"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Registrierungseinträge"
  - "Registrierungseinträge [Office-Entwicklung in Visual Studio]"
ms.assetid: 319e5bbc-0234-4af0-91ce-54bcfafc173f
caps.latest.revision: 79
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 78
---
# Registrierungseintr&#228;ge f&#252;r VSTO-Add-Ins
  Sie müssen einen bestimmten Satz von Registrierungseinträgen erstellen, wenn Sie VSTO\-Add\-Ins bereitstellen, die mithilfe von Visual Studio erstellt werden. Diese Registrierungseinträge enthalten Informationen, mit denen die Microsoft Office\-Anwendung das VSTO\-Add\-In erkennt und lädt.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Beim Erstellen des Projekts erstellt Visual Studio diese Registrierungseinträge auf dem Entwicklungscomputer, sodass Sie das VSTO\-Add\-In einfach ausführen und debuggen können. Wenn Sie das VSTO\-Add\-In mithilfe von ClickOnce bereitstellen, werden die Registrierungseinträge automatisch auf dem Endbenutzercomputer erstellt. Wenn Sie Windows Installer verwenden, um das VSTO\-Add\-In bereitzustellen, müssen Sie das InstallShield Limited\-Edition\-Projekt konfigurieren, um die Registrierungseinträge auf dem Endbenutzercomputer zu erstellen.  
  
 Weitere Informationen zur Verwendung der Registrierungseinträge während des Ladevorgangs für VSTO\-Add\-Ins finden Sie unter [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  In diesem Thema stellt der Text *Add\-In\-ID* eine eindeutige ID für das VSTO\-Add\-In dar. Standardmäßig entspricht die ID dem Namen der VSTO\-Add\-In\-Assembly.  
  
## Registrieren von VSTO\-Add\-Ins für den aktuellen Benutzer im Vergleich zu allen Benutzern  
 Wenn ein VSTO\-Add\-In installiert ist, kann es auf zwei Arten registriert werden:  
  
-   Nur für den aktuellen Benutzer \(es ist nur für den Benutzer verfügbar, der bei Installation des VSTO\-Add\-Ins auf dem Computer angemeldet ist\). In diesem Fall werden die Registrierungseinträge unter HKEY\_CURRENT\_USER erstellt.  
  
-   Für alle Benutzer \(jeder auf dem Computer angemeldete Benutzer kann das VSTO\-Add\-In verwenden\). In diesem Fall werden die Registrierungseinträge unter HKEY\_LOCAL\_MACHINE erstellt.  
  
 Alle VSTO\-Add\-Ins, die Sie mit Visual Studio erstellen, können für den aktuellen Benutzer registriert werden. VSTO\-Add\-Ins können für alle Benutzer jedoch nur in bestimmten Szenarien registriert werden. Diese Szenarien hängen von der Version von Microsoft Office auf dem Computer und davon ab, wie das VSTO\-Add\-In bereitgestellt wurde.  
  
### Microsoft Office\-Version  
 In Office\-Anwendungen können VSTO\-Add\-Ins geladen werden, die unter HKEY\_LOCAL\_MACHINE oder HKEY\_CURRENT\_USER registriert werden.  
  
 Um VSTO\-Add\-Ins zu laden, die unter HKEY\_LOCAL\_MACHINE registriert werden, muss das Updatepaket 976477 auf den Computern installiert sein. Weitere Informationen finden Sie unter [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=184923](http://go.microsoft.com/fwlink/?LinkId=184923).  
  
### Bereitstellungstyp  
 Wenn Sie ClickOnce verwenden, um ein VSTO\-Add\-In bereitzustellen, kann das VSTO\-Add\-In nur für den aktuellen Benutzer registriert werden. Dies liegt daran, dass ClickOnce nur das Erstellen von Schlüsseln unter HKEY\_CURRENT\_USER unterstützt. Wenn Sie ein VSTO\-Add\-In für alle Benutzer auf einem Computer registrieren möchten, müssen Sie Windows Installer verwenden, um das VSTO\-Add\-In bereitzustellen. Weitere Informationen zu diesen Bereitstellungstypen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) und [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## Registrierungseinträge  
 Die erforderlichen VSTO\-Add\-In\-Registrierungseinträge befinden sich für alle Anwendungen mit Ausnahme von Visio unter dem folgenden Registrierungsschlüssel, wobei *Root* HKEY\_CURRENT\_USER oder HKEY\_LOCAL\_MACHINE ist.  
  
 **Alle Anwendungen mit Ausnahme von Visio**  
  
|Office\-Version|Konfigurationspfad|  
|---------------------|------------------------|  
|32\-Bit|*Root*\\Software\\Microsoft\\Office\\*Anwendungsname*\\Addins\\*Add\-In\-ID*|  
|64\-Bit|*Root*\\Software\\Wow6432Node\\Microsoft\\Office\\*Anwendungsname*\\Addins\\*Add\-In\-ID*|  
  
 **Visio**  
  
|Office\-Version|Konfigurationspfad|  
|---------------------|------------------------|  
|32\-Bit|*Root*\\Software\\Microsoft\\Visio\\Addins\\*Add\-In\-ID*|  
|64\-Bit|*Root*\\Software\\Wow6432Node\\Visio\\Addins\\*Add\-In\-ID*|  
  
 In der folgenden Tabelle werden die Einträge in diesem Registrierungsschlüssel aufgeführt.  
  
|Eingabe|Typ|Wert|  
|-------------|---------|----------|  
|**Description**|REG\_SZ|Erforderlich. Eine kurze Beschreibung des VSTO\-Add\-Ins.<br /><br /> Diese Beschreibung wird angezeigt, wenn der Benutzer das VSTO\-Add\-In in der Microsoft Office\-Anwendung im Dialogfeld **Optionen** im Bereich **Add\-Ins** auswählt.|  
|**FriendlyName**|REG\_SZ|Erforderlich. Ein beschreibender Name des VSTO\-Add\-Ins, der in der Microsoft Office\-Anwendung im Dialogfeld **COM\-Add\-Ins** angezeigt wird. Der Standardwert ist die ID des VSTO\-Add\-Ins.|  
|**LoadBehavior**|REG\_DWORD|Erforderlich. Ein Wert, der zusätzlich zum aktuellen Zustand des VSTO\-Add\-Ins \(geladen oder entladen\) angibt, wann die Anwendung das VSTO\-Add\-In laden soll.<br /><br /> Standardmäßig ist dieser Wert auf 3 festgelegt, was bedeutet, dass das VSTO\-Add\-In beim Start geladen wird. Weitere Informationen finden Sie unter [LoadBehavior\-Werte](#LoadBehavior). **Note:**  Wenn ein Benutzer das VSTO\-Add\-In deaktiviert, wird mit dieser Aktion der **LoadBehavior**\-Wert in der Registrierungsstruktur HKEY\_CURRENT\_USER geändert. Für jeden Benutzer wird der in der HKEY\_LOCAL\_MACHINE\-Struktur definierte **LoadBehavior**\-Standardwert mit dem **LoadBehavior**\-Wert in der HKEY\_CURRENT\_USER\-Struktur überschrieben.|  
|**Manifest**|REG\_SZ|Erforderlich. Der vollständige Pfad des Bereitstellungsmanifests für das VSTO\-Add\-In. Bei dem Pfad kann es sich um einen Speicherort auf dem lokalen Computer, eine Netzwerkfreigabe \(UNC\) oder um einen Webserver \(HTTP\) handeln.<br /><br /> Wenn Sie die Projektmappe mit Windows Installer bereitstellen, müssen Sie dem Pfad das Präfix **file:\/\/\/Manifest** hinzufügen. Außerdem müssen Sie die Zeichenfolge **&#124;vstolocal** \(d. h. das Pipezeichen **&#124;** gefolgt von **vstolocal**\) am Ende dieses Pfads anfügen. Dadurch wird sichergestellt, dass die Projektmappe aus dem Installationsordner geladen wird und nicht aus dem ClickOnce\-Cache. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Note:**  Wenn Sie ein VSTO\-Add\-In auf dem Entwicklungscomputer erstellen, fügt Visual Studio automatisch die **&#124;vstolocal**\-Zeichenfolge an diesen Registrierungseintrag an.|  
  
###  <a name="OutlookEntries"></a> Registrierungseinträge für Outlook\-Formularbereiche  
 Wenn Sie einen benutzerdefinierten Formularbereich in einem VSTO\-Add\-In für Outlook erstellen, werden zusätzliche Registrierungseinträge verwendet, um den Formularbereich für Outlook zu registrieren. Diese Einträge werden unter einem anderen Registrierungsschlüssel für jede Nachrichtenklasse erstellt, die vom Formularbereich unterstützt wird. Diese Registrierungsschlüssel befinden sich am folgenden Speicherort, wobei *Stamm* HKEY\_CURRENT\_USER oder HKEY\_LOCAL\_MACHINE ist.  
  
 *Root*\\Software\\Microsoft\\Office\\Outlook\\FormRegions\\*Nachrichtenklasse*  
  
 Wie die anderen von allen VSTO\-Add\-Ins verwendeten Registrierungseinträge erstellt auch Visual Studio beim Erstellen des Projekts die Formularbereich\-Registrierungseinträge auf dem Entwicklungscomputer. Wenn Sie das VSTO\-Add\-In mithilfe von ClickOnce bereitstellen, werden die Registrierungseinträge automatisch auf dem Endbenutzercomputer erstellt. Wenn Sie Windows Installer verwenden, um das VSTO\-Add\-In bereitzustellen, müssen Sie das InstallShield Limited\-Edition\-Projekt konfigurieren, um die Registrierungseinträge auf dem Endbenutzercomputer zu erstellen.  
  
 Weitere Informationen zu den Formularbereichsregistrierungseinträgen finden Sie unter [Angeben von Formularbereichen in der Windows\-Registrierung](HV10038637). Weitere Informationen zu Outlook\-Formularbereichen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="LoadBehavior"></a> LoadBehavior\-Werte  
 Der **LoadBehavior**\-Eintrag unter dem Schlüssel *Root*\\Software\\Microsoft\\Office\\*Anwendungsname*\\Addins\\*Add\-In\-ID* enthält eine bitweise Kombination von Werten, die das Laufzeitverhalten des VSTO\-Add\-Ins angeben. Das Bit der niedrigsten Ordnung \(Werte 0 und 1\) gibt an, ob das VSTO\-Add\-In gerade geladen ist. Andere Bits geben an, wann die Anwendung versucht, das VSTO\-Add\-In zu laden.  
  
 In der Regel soll der **LoadBehavior**\-Eintrag auf 0, 3 oder 16 \(dezimal\) festgelegt werden, wenn das VSTO\-Add\-In auf Endbenutzercomputern installiert wird. Standardmäßig legt Visual Studio den **LoadBehavior**\-Eintrag des VSTO\-Add\-Ins auf 3 fest, wenn Sie es erstellen oder veröffentlichen.  
  
 In der folgenden Tabelle sind alle möglichen Werte für den **LoadBehavior**\-Eintrag aufgeführt. Einige Beschreibungen in dieser Tabelle verweisen auf das manuelle oder programmgesteuerte Laden eines VSTO\-Add\-Ins. Um ein VSTO\-Add\-In manuell zu laden, aktivieren Sie das Kontrollkästchen neben dem VSTO\-Add\-In im Dialogfeld **COM\-Add\-Ins** in der Anwendung. Um ein VSTO\-Add\-In programmgesteuert zu laden, legen Sie die <xref:Microsoft.Office.Core.COMAddIn.Connect%2A>\-Eigenschaft des <xref:Microsoft.Office.Core.COMAddIn>\-Objekts, mit dem das VSTO\-Add\-In dargestellt wird, auf **true** fest.  
  
|Dezimalwert|VSTO\-Add\-In\-Status|VSTO\-Add\-In\-Ladeverhalten|Beschreibung|  
|-----------------|---------------------------|----------------------------------|------------------|  
|0|Nicht Geladen|Nicht automatisch laden|Die Anwendung versucht nie, das VSTO\-Add\-In beim Start automatisch zu laden. Der Benutzer kann das VSTO\-Add\-In manuell laden, oder das VSTO\-Add\-In kann programmgesteuert geladen werden.<br /><br /> Wenn das VSTO\-Add\-In erfolgreich geladen wird, bleibt der **LoadBehavior**\-Wert 0. Der Status des VSTO\-Add\-Ins im Dialogfeld **COM\-Add\-Ins** wird aber aktualisiert, um anzugeben, dass das VSTO\-Add\-In geladen wird.|  
|1|Geladen|Nicht automatisch laden|Die Anwendung versucht nie, das VSTO\-Add\-In beim Start automatisch zu laden. Der Benutzer kann das VSTO\-Add\-In manuell laden, oder das VSTO\-Add\-In kann programmgesteuert geladen werden.<br /><br /> Obwohl im Dialogfeld **COM\-Add\-Ins** angegeben ist, dass das VSTO\-Add\-In geladen wird, nachdem die Anwendung gestartet wurde, wird das VSTO\-Add\-In eigentlich erst geladen, wenn es manuell oder programmgesteuert geladen wird.<br /><br /> Wenn die Anwendung das VSTO\-Add\-In erfolgreich lädt, ändert sich der **LoadBehavior**\-Wert in 0 und bleibt nach dem Schließen der Anwendung weiterhin 0.|  
|2|Nicht Geladen|Beim Starten laden|Die Anwendung versucht nicht, das VSTO\-Add\-In beim Start automatisch zu laden. Der Benutzer kann das VSTO\-Add\-In manuell laden, oder das VSTO\-Add\-In kann programmgesteuert geladen werden.<br /><br /> Wenn die Anwendung das VSTO\-Add\-In erfolgreich lädt, ändert sich der **LoadBehavior**\-Wert in 3 und bleibt nach dem Schließen der Anwendung weiterhin 3.|  
|3|Geladen|Beim Starten laden|Die Anwendung versucht, das VSTO\-Add\-In beim Starten zu laden. Dies ist der Standardwert, wenn Sie ein VSTO\-Add\-In in Visual Studio erstellen oder veröffentlichen.<br /><br /> Wenn die Anwendung das VSTO\-Add\-In erfolgreich lädt, bleibt der **LoadBehavior**\-Wert 3. Wenn beim Laden des VSTO\-Add\-Ins ein Fehler auftritt, ändert sich der **LoadBehavior**\-Wert in 2 und bleibt nach dem Schließen der Anwendung weiterhin 2.|  
|8|Nicht Geladen|Bedarfsgesteuert laden|Die Anwendung versucht nicht, das VSTO\-Add\-In beim Start automatisch zu laden. Der Benutzer kann das VSTO\-Add\-In manuell laden, oder das VSTO\-Add\-In kann programmgesteuert geladen werden.<br /><br /> Wenn die Anwendung das VSTO\-Add\-In erfolgreich lädt, ändert sich der **LoadBehavior**\-Wert in 9.|  
|9|Geladen|Bedarfsgesteuert laden|Das VSTO\-Add\-In wird nur geladen, wenn es für die Anwendung notwendig ist, z. B. wenn ein Benutzer auf ein Benutzeroberflächenelement klickt, das auf Funktionen im VSTO\-Add\-In zurückgreift \(z. B. eine benutzerdefinierte Schaltfläche im Menüband\).<br /><br /> Wenn die Anwendung das VSTO\-Add\-In erfolgreich lädt, bleibt der **LoadBehavior**\-Wert 9. Der Status des VSTO\-Add\-Ins im Dialogfeld **COM\-Add\-Ins** wird aber aktualisiert, um anzugeben, dass das VSTO\-Add\-In momentan geladen ist. Wenn beim Laden des VSTO\-Add\-Ins ein Fehler auftritt, ändert sich der **LoadBehavior**\-Wert in 8.|  
|16|Geladen|Beim ersten Mal laden, dann bedarfsgesteuert laden|Legen Sie diesen Wert fest, wenn Sie das VSTO\-Add\-In bedarfsgesteuert laden möchten. Die Anwendung lädt das VSTO\-Add\-In, wenn der Benutzer die Anwendung das erste Mal ausführt. Beim nächsten Ausführen lädt die Anwendung alle Benutzeroberflächenelemente, die durch das VSTO\-Add\-In definiert werden. Das VSTO\-Add\-In wird aber erst dann geladen, wenn der Benutzer auf ein Benutzeroberflächenelement klickt, das dem VSTO\-Add\-In zugeordnet ist.<br /><br /> Wenn die Anwendung das VSTO\-Add\-In zum ersten Mal erfolgreich lädt, bleibt der **LoadBehavior**\-Wert 16, während das VSTO\-Add\-In geladen ist. Nachdem die Anwendung geschlossen wurde, ändert sich der **LoadBehavior**\-Wert in 9.|  
  
## Siehe auch  
 [Architektur von Office-Projektmappen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  