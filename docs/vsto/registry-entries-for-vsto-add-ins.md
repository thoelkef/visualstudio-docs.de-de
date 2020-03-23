---
title: Registrierungseinträge für VSTO-Add-Ins
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b02b50c42692ec2fd455358df5157e0b8481562b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416522"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Registrierungseinträge für VSTO-Add-Ins
  Sie müssen einen bestimmten Satz von Registrierungseinträgen erstellen, wenn Sie VSTO-Add-Ins bereitstellen, die mithilfe von Visual Studio erstellt werden. Diese Registrierungseinträge enthalten Informationen, mit denen die Microsoft Office-Anwendung das VSTO-Add-In erkennt und lädt.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Beim Erstellen des Projekts erstellt Visual Studio diese Registrierungseinträge auf dem Entwicklungscomputer, sodass Sie das VSTO-Add-In einfach ausführen und debuggen können. Wenn Sie ClickOnce zum Bereitstellen Ihres VSTO-Add-Ins verwenden, werden die Registrierungseinträge automatisch auf dem Endbenutzercomputer erstellt. Wenn Sie Windows Installer zum Bereitstellen Ihres VSTO-Add-Ins verwenden, müssen Sie das InstallShield Limited Edition-Projekt so konfigurieren, dass die Registrierungseinträge auf dem Endbenutzercomputer erstellt werden.

 Weitere Informationen zur Verwendung der Registrierungseinträge während des Ladevorgangs für VSTO-Add-Ins finden Sie unter [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> In diesem Thema stellt der Text *Add-In-ID* eine eindeutige ID für das VSTO-Add-In dar. Standardmäßig entspricht die ID dem Namen der VSTO-Add-In-Assembly.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrieren von VSTO-Add-Ins für den aktuellen Benutzer im Vergleich zu allen Benutzern
 Wenn ein VSTO-Add-In installiert ist, kann es auf zwei Arten registriert werden:

- Nur für den aktuellen Benutzer (d. h., er steht nur dem Benutzer zur Verfügung, der am Computer angemeldet ist, wenn das VSTO-Add-In installiert ist). In diesem Fall werden die Registrierungseinträge unter der **HKEY_CURRENT_USER**erstellt.

- Für alle Benutzer (d. h. jeder Benutzer, der sich am Computer anmeldet, kann das VSTO-Add-In verwendet werden). In diesem Fall werden die Registrierungseinträge unter **HKEY_LOCAL_MACHINE**erstellt.

  Alle VSTO-Add-Ins, die Sie mit Visual Studio erstellen, können für den aktuellen Benutzer registriert werden. VSTO-Add-Ins können für alle Benutzer jedoch nur in bestimmten Szenarien registriert werden. Diese Szenarien hängen von der Version von Microsoft Office auf dem Computer und davon ab, wie das VSTO-Add-In bereitgestellt wurde.

### <a name="deployment-type"></a>Bereitstellungstyp
 Wenn Sie ClickOnce verwenden, um ein VSTO-Add-In bereitzustellen, kann das VSTO-Add-In nur für den aktuellen Benutzer registriert werden. Dies liegt daran, dass ClickOnce nur das Erstellen von Schlüsseln unter **HKEY_CURRENT_USER**unterstützt. Wenn Sie ein VSTO-Add-In für alle Benutzer auf einem Computer registrieren möchten, müssen Sie Windows Installer verwenden, um das VSTO-Add-In bereitzustellen. Weitere Informationen zu diesen Bereitstellungstypen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) und [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Registrierungseinträge
 Die erforderlichen VSTO-Add-In-Registrierungseinträge befinden sich unter den folgenden Registrierungsschlüsseln, bei denen *Root* **HKEY_CURRENT_USER** oder **HKEY_LOCAL_MACHINE** ist, je nachdem, ob die Installation für den aktuellen Benutzer oder alle Benutzer erfolgt.

|Office-Anwendung|Konfigurationspfad|
|------------------|------------------|
|Visio|*Stamm-,* Software-, Microsoft\\*Visio-Add-Ins-Add-In-ID*\\*add-in ID*|
|Alle anderen|*Root-Anwendungsname für die Datei "Software"* und "Microsoft" und "Office\\*Office"*\\ *"Addins"-Add-In-ID*|

> [!NOTE]
> Wenn das Installationsprogramm auf alle Benutzer unter 64-Bit-Windows abzielt, wird empfohlen, dass es zwei Registrierungseinträge\\enthält, einen unter der HKEY_LOCAL_MACHINE-Software-Microsoft und einen unter der HKEY_LOCAL_MACHINE-Software-WOW6432-Knoten-Microsoft-Struktur.**WOW6432Node** Dies liegt daran, dass es Benutzern möglich ist, entweder 32-Bit- oder 64-Bit-Versionen von Office auf dem Computer zu verwenden.
>
>Wenn der Installer auf den aktuellen Benutzer abzielt, muss er nicht auf dem WOW6432Node installiert werden, da der Pfad HKEY_CURRENT_USER-Software freigegeben ist.
>
>Weitere Informationen finden Sie [unter 32-Bit- und 64-Bit-Anwendungsdaten in der Registrierung](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 In der folgenden Tabelle werden die Einträge in diesem Registrierungsschlüssel aufgeführt.

|Eintrag|type|value|
|-----------|----------|-----------|
|**Beschreibung**|REG_SZ|Erforderlich. Eine kurze Beschreibung des VSTO-Add-Ins.<br /><br /> Diese Beschreibung wird angezeigt, wenn der Benutzer das VSTO-Add-In in der Microsoft Office-Anwendung im Dialogfeld **Optionen** im Bereich **Add-Ins** auswählt.|
|**Friendlyname**|REG_SZ|Erforderlich. Ein beschreibender Name des VSTO-Add-Ins, der in der Microsoft Office-Anwendung im Dialogfeld **COM-Add-Ins** angezeigt wird. Der Standardwert ist die ID des VSTO-Add-Ins.|
|**LoadBehavior**|REG_DWORD|Erforderlich. Ein Wert, der zusätzlich zum aktuellen Zustand des VSTO-Add-Ins (geladen oder entladen) angibt, wann die Anwendung das VSTO-Add-In laden soll.<br /><br /> Standardmäßig ist dieser Wert auf 3 festgelegt, was bedeutet, dass das VSTO-Add-In beim Start geladen wird. Weitere Informationen finden Sie unter [LoadBehavior-Werte](#LoadBehavior). **Hinweis:**  Wenn ein Benutzer das VSTO-Add-In deaktiviert, ändert diese Aktion den **LoadBehavior-Wert** in der HKEY_CURRENT_USER-Registrierungsstruktur. **HKEY_CURRENT_USER** Für jeden Benutzer überschreibt der Wert des **LoadBehavior-Werts** in der HKEY_CURRENT_USER-Struktur die standardmäßige **LoadBehavior-Definition,** die in der **HKEY_LOCAL_MACHINE-Struktur** definiert ist.|
|**Manifest**|REG_SZ|Erforderlich. Der vollständige Pfad des Bereitstellungsmanifests für das VSTO-Add-In. Bei dem Pfad kann es sich um einen Speicherort auf dem lokalen Computer, eine Netzwerkfreigabe (UNC) oder um einen Webserver (HTTP) handeln.<br /><br /> Wenn Sie Windows Installer zum Bereitstellen der Lösung verwenden, müssen Sie das Präfix **file:///** zum **Manifestpfad** hinzufügen. Sie müssen auch die Zeichenfolge **&#124;vstolocal** (d. h. das&#124;**gefolgt** von **vstolocal)** an das Ende dieses Pfads anhängen. Dadurch wird sichergestellt, dass die Projektmappe aus dem Installationsordner geladen wird und nicht aus dem ClickOnce-Cache. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md). **Hinweis:**  Wenn Sie ein VSTO-Add-In auf dem Entwicklungscomputer erstellen, fügt Visual Studio die **&#124;vstolocal-Zeichenfolge** automatisch an diesen Registrierungseintrag an.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Registrierungseinträge für Outlook-Formularbereiche
 Wenn Sie einen benutzerdefinierten Formularbereich in einem VSTO-Add-In für Outlook erstellen, werden zusätzliche Registrierungseinträge verwendet, um den Formularbereich für Outlook zu registrieren. Diese Einträge werden unter einem anderen Registrierungsschlüssel für jede Nachrichtenklasse erstellt, die vom Formularbereich unterstützt wird. Diese Registrierungsschlüssel befinden sich am folgenden Speicherort, an dem *Root* **HKEY_CURRENT_USER** oder **HKEY_LOCAL_MACHINE**ist.

 *Nachrichtenklasse "Root"*, "Software"\\und "Microsoft" und "Outlook" und "FormularRegions"-Nachrichtenklasse*message class*

 Wie die anderen von allen VSTO-Add-Ins verwendeten Registrierungseinträge erstellt auch Visual Studio beim Erstellen des Projekts die Formularbereich-Registrierungseinträge auf dem Entwicklungscomputer. Wenn Sie ClickOnce zum Bereitstellen Ihres VSTO-Add-Ins verwenden, werden die Registrierungseinträge automatisch auf dem Endbenutzercomputer erstellt. Wenn Sie Windows Installer zum Bereitstellen Ihres VSTO-Add-Ins verwenden, müssen Sie das InstallShield Limited Edition-Projekt so konfigurieren, dass die Registrierungseinträge auf dem Endbenutzercomputer erstellt werden.

 Weitere Informationen zu den Registrierungseinträgen für Formularregion finden Sie unter [Angeben des Speicherorts eines Formularbereichs in einem benutzerdefinierten Formular](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Weitere Informationen zu Outlook-Formularbereichen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a>LoadBehavior-Werte
 Der **LoadBehavior-Eintrag** unter dem Anwendungsnamen\\ *"Root"*(Root-Software-Microsoft-Office-Anwendungstaste,\\*Addins-Add-In-ID-Taste)* enthält eine bitweise Kombination von Werten, die das Laufzeitverhalten des VSTO-Add-Ins angeben.*application name* Das Bit der niedrigsten Ordnung (Werte 0 und 1) gibt an, ob das VSTO-Add-In gerade geladen ist. Andere Bits geben an, wann die Anwendung versucht, das VSTO-Add-In zu laden.

 In der Regel ist der **LoadBehavior-Eintrag** auf 0, 3 oder 16 (dezimal) festgelegt, wenn das VSTO-Add-In auf Endbenutzercomputern installiert ist. Standardmäßig legt Visual Studio den **LoadBehavior** -Eintrag des VSTO-Add-Ins auf 3 fest, wenn Sie es erstellen oder veröffentlichen.

 In der folgenden Tabelle sind alle möglichen Werte für den **LoadBehavior** -Eintrag aufgeführt. Einige Beschreibungen in dieser Tabelle verweisen auf das manuelle oder programmgesteuerte Laden eines VSTO-Add-Ins. Um ein VSTO-Add-In manuell zu laden, aktivieren Sie das Kontrollkästchen neben dem VSTO-Add-In im Dialogfeld **COM-Add-Ins** in der Anwendung. Um ein VSTO-Add-In programmgesteuert zu laden, legen Sie die <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> -Eigenschaft des <xref:Microsoft.Office.Core.COMAddIn> -Objekts, mit dem das VSTO-Add-In dargestellt wird, auf **true**.

|Dezimalwert|VSTO-Add-In-Status|VSTO-Add-In-Ladeverhalten|Beschreibung|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Nicht Geladen|Nicht automatisch laden|Die Anwendung versucht nie, das VSTO-Add-In beim Start automatisch zu laden. Der Benutzer kann das VSTO-Add-In manuell laden, oder das VSTO-Add-In kann programmgesteuert geladen werden.<br /><br /> Wenn das VSTO-Add-In erfolgreich geladen wird, bleibt der **LoadBehavior** -Wert 0. Der Status des VSTO-Add-Ins im Dialogfeld **COM-Add-Ins** wird aber aktualisiert, um anzugeben, dass das VSTO-Add-In geladen wird.|
|1|Geladen|Nicht automatisch laden|Die Anwendung versucht nie, das VSTO-Add-In beim Start automatisch zu laden. Der Benutzer kann das VSTO-Add-In manuell laden, oder das VSTO-Add-In kann programmgesteuert geladen werden.<br /><br /> Obwohl das Dialogfeld **COM-Add-Ins** angibt, dass das VSTO-Add-In nach dem Starten der Anwendung geladen wird, wird das VSTO-Add-In erst geladen, wenn es manuell oder programmgesteuert geladen wird.<br /><br /> Wenn die Anwendung das VSTO-Add-In erfolgreich lädt, ändert sich der **LoadBehavior** -Wert in 0 und bleibt nach dem Schließen der Anwendung weiterhin 0.|
|2|Nicht Geladen|Beim Starten laden|Die Anwendung versucht nicht, das VSTO-Add-In beim Start automatisch zu laden. Der Benutzer kann das VSTO-Add-In manuell laden, oder das VSTO-Add-In kann programmgesteuert geladen werden.<br /><br /> Wenn die Anwendung das VSTO-Add-In erfolgreich lädt, ändert sich der **LoadBehavior** -Wert in 3 und bleibt nach dem Schließen der Anwendung weiterhin 3.|
|3|Geladen|Beim Starten laden|Die Anwendung versucht, das VSTO-Add-In beim Starten zu laden. Dies ist der Standardwert, wenn Sie ein VSTO-Add-In in Visual Studio erstellen oder veröffentlichen.<br /><br /> Wenn die Anwendung das VSTO-Add-In erfolgreich lädt, bleibt der **LoadBehavior** -Wert 3. Wenn beim Laden des VSTO-Add-Ins ein Fehler auftritt, ändert sich der **LoadBehavior** -Wert in 2 und bleibt nach dem Schließen der Anwendung weiterhin 2.|
|8|Nicht Geladen|Bedarfsgesteuert laden|Die Anwendung versucht nicht, das VSTO-Add-In beim Start automatisch zu laden. Der Benutzer kann das VSTO-Add-In manuell laden, oder das VSTO-Add-In kann programmgesteuert geladen werden.<br /><br /> Wenn die Anwendung das VSTO-Add-In erfolgreich lädt, ändert sich der **LoadBehavior** -Wert in 9.|
|9|Geladen|Bedarfsgesteuert laden|Das VSTO-Add-In wird nur geladen, wenn es für die Anwendung notwendig ist, z. B. wenn ein Benutzer auf ein Benutzeroberflächenelement klickt, das auf Funktionen im VSTO-Add-In zurückgreift (z. B. eine benutzerdefinierte Schaltfläche im Menüband).<br /><br /> Wenn die Anwendung das VSTO-Add-In erfolgreich lädt, bleibt der **LoadBehavior** -Wert 9. Der Status des VSTO-Add-Ins im Dialogfeld **COM-Add-Ins** wird aber aktualisiert, um anzugeben, dass das VSTO-Add-In momentan geladen ist. Wenn beim Laden des VSTO-Add-Ins ein Fehler auftritt, ändert sich der **LoadBehavior** -Wert in 8.|
|16|Geladen|Beim ersten Mal laden, dann bedarfsgesteuert laden|Legen Sie diesen Wert fest, wenn Sie das VSTO-Add-In bedarfsgesteuert laden möchten. Die Anwendung lädt das VSTO-Add-In, wenn der Benutzer die Anwendung das erste Mal ausführt. Beim nächsten Ausführen lädt die Anwendung alle Benutzeroberflächenelemente, die durch das VSTO-Add-In definiert werden. Das VSTO-Add-In wird aber erst dann geladen, wenn der Benutzer auf ein Benutzeroberflächenelement klickt, das dem VSTO-Add-In zugeordnet ist.<br /><br /> Wenn die Anwendung das VSTO-Add-In zum ersten Mal erfolgreich lädt, bleibt der **LoadBehavior** -Wert 16, während das VSTO-Add-In geladen ist. Nachdem die Anwendung geschlossen wurde, ändert sich der **LoadBehavior** -Wert in 9.|

## <a name="see-also"></a>Weitere Informationen
- [Architektur von Office-Lösungen in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Erstellen von Office-Lösungen](../vsto/building-office-solutions.md)
- [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)
 