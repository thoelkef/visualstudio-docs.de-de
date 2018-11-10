---
title: 'Gewusst wie: Verwalten von Dienstkonfigurationen und Profilen | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie mit Dienstkonfigurationen und profilkonfigurationsdateien Dienstkonfigurationsdateien arbeiten | die Einstellungen für die bereitstellungsumgebungen gespeichert und die veröffentlichungseinstellungen für Clouddienste.
author: ghogen
manager: douge
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 3f7c7341b115f0899ac4c90d574a65dfdb4087bc
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001993"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Verwalten von Dienstkonfigurationen und -profilen
## <a name="overview"></a>Übersicht
Wenn Sie einen Cloud-Dienst veröffentlichen, speichert Visual Studio Konfigurationsinformationen in zwei Arten von Konfigurationsdateien: Dienstkonfigurationen und Profile. Dienstkonfigurationen (cscfg-Dateien) werden Einstellungen für die bereitstellungsumgebungen für einen Azure-Cloud-Dienst gespeichert. Azure verwendet diese Konfigurationsdateien, bei der Verwaltung Ihrer Cloud-Dienste. Auf der anderen Seite Profilspeicher (azurepubxml-Dateien) veröffentlichungseinstellungen für Clouddienste. Diese Einstellungen werden bei der Sie den Veröffentlichungs-Assistenten verwenden und lokal von Visual Studio verwendet werden. In diesem Thema wird erläutert, wie funktioniert mit beiden Arten von Konfigurationsdateien wird.

## <a name="service-configurations"></a>Dienstkonfigurationen
Sie können mehrere Dienstkonfigurationen verwenden Sie für jede Ihrer bereitstellungsumgebungen erstellen. Beispielsweise können Sie eine Dienstkonfiguration für die lokale Umgebung erstellen, die Sie zum Ausführen und Testen einer Azure-Anwendung und eine andere Dienstkonfiguration für Ihre produktionsumgebung verwenden.

Sie können das Hinzufügen, löschen, umbenennen und diese Dienstkonfigurationen basierend auf Ihren Anforderungen ändern. Sie können diese Dienstkonfigurationen in Visual Studio verwalten, wie in der folgenden Abbildung dargestellt.

![Dienstkonfigurationen verwalten](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

Sie können auch öffnen, die **Konfigurationen verwalten** Dialogfeld Eigenschaftenseiten der Rolle. Um die Eigenschaften für eine Rolle im Azure-Projekt zu öffnen, öffnen Sie das Kontextmenü für diese Rolle, und wählen Sie dann **Eigenschaften**. Auf der **Einstellungen** Registerkarte, erweitern Sie die **Dienstkonfiguration** aus, und wählen Sie dann **verwalten** zum Öffnen der **Konfigurationen verwalten** Das Dialogfeld.

### <a name="to-add-a-service-configuration"></a>Hinzufügen eine Dienstkonfiguration
1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Azure-Projekt, und wählen Sie dann **Konfigurationen verwalten**.
   
    Die **Dienstkonfigurationen verwalten** Dialogfeld wird angezeigt.
2. Um eine Dienstkonfiguration hinzuzufügen, müssen Sie eine Kopie einer vorhandenen Konfiguration erstellen. Wählen Sie die Konfiguration, die Sie verwenden möchten, kopieren Sie aus der Liste aus, und wählen Sie dann zu diesem Zweck **Kopie erstellen**.
3. (Optional) Um der Dienstkonfiguration einen anderen Namen geben, wählen Sie die neue Dienstkonfiguration in der Liste der Namen, und wählen Sie dann **umbenennen**. In der **Namen** Text geben den Namen, die Sie möchten für diese Dienstkonfiguration verwenden, und wählen Sie dann **OK**.
   
    Eine neue Dienstkonfigurationsdatei mit dem Namen ServiceConfiguration. [Neuer Name] .cscfg zum Azure-Projekt im Projektmappen-Explorer hinzugefügt wird.

### <a name="to-delete-a-service-configuration"></a>So löschen Sie eine Dienstkonfiguration
1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Azure-Projekt, und wählen Sie dann **Konfigurationen verwalten**.
   
    Die **Dienstkonfigurationen verwalten** Dialogfeld wird angezeigt.
2. Wählen Sie zum Löschen einer Dienstkonfiguration die Konfiguration, die Sie aus löschen möchten die **Namen** aus, und wählen Sie dann **entfernen**. Ein Dialogfeld wird angezeigt, um sicherzustellen, dass Sie diese Konfiguration wirklich löschen möchten.
3. Wählen Sie **löschen**.
   
     Die Dienstkonfigurationsdatei wird aus dem Azure-Projekt im Projektmappen-Explorer entfernt.

### <a name="to-rename-a-service-configuration"></a>Zum Umbenennen einer Dienstkonfiguration
1. Klicken Sie im Projektmappen-Explorer öffnen Sie das Kontextmenü für das Azure-Projekt, und wählen Sie dann **Konfigurationen verwalten**.
   
    Die **Dienstkonfigurationen verwalten** Dialogfeld wird angezeigt.
2. Wählen Sie zum Umbenennen einer Dienstkonfiguration die neue Dienstkonfiguration in der **Namen** aus, und wählen Sie dann **umbenennen**. In der **Namen** Text geben den Namen, die Sie verwenden möchten, für diese Dienstkonfiguration verwenden, und wählen Sie dann **OK**.
   
    Der Name der Dienstkonfigurationsdatei wird im Azure-Projekt im Projektmappen-Explorer geändert.

### <a name="to-change-a-service-configuration"></a>So ändern Sie eine Dienstkonfiguration
* Wenn Sie eine Dienstkonfiguration ändern möchten, öffnen Sie das Kontextmenü für die jeweilige Rolle, die Sie verwenden möchten, ändern Sie im Azure-Projekt, und wählen Sie dann **Eigenschaften**. Finden Sie unter [Vorgehensweise: Konfigurieren der Rollen für Azure-Clouddienst mit Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md) für Weitere Informationen.

## <a name="make-different-setting-combinations-by-using-profiles"></a>Erstellen Sie verschiedener Einstellungskombinationen mithilfe von Profilen
Mithilfe eines Profils können Sie automatisch in eingeben der **Veröffentlichungs-Assistenten** mit verschiedenen Kombinationen von Einstellungen für unterschiedliche Zwecke. Beispielsweise haben Sie ein Profil für debugging und ein weiteres für erstellt. In diesem Fall Ihre **Debuggen** -Profil **IntelliTrace** aktiviert und die **Debuggen** -Konfiguration ausgewählt, und Ihre **Version** Profil **IntelliTrace** deaktiviert und die **Version** ausgewählte Konfiguration. Sie können auch verschiedene Profile verwenden, um einen Dienst unter Verwendung eines anderen Speicherkontos bereitzustellen.

Wenn Sie den Assistenten zum ersten Mal ausführen, wird ein Standardprofil erstellt. Visual Studio speichert das Profil in eine Datei mit der azurepubxml-Erweiterung, die unter Ihrem Azure-Projekt hinzugefügt wird die **Profile** Ordner. Wenn Sie den Assistenten später ausführen manuell andere Optionen angeben, wird die Datei automatisch aktualisiert. Bevor Sie das folgende Verfahren ausführen, sollten Sie bereits Ihren Cloud-Dienst mindestens einmal veröffentlicht haben.

### <a name="to-add-a-profile"></a>Hinzufügen eines Profils
1. Öffnen Sie das Kontextmenü für Ihr Azure-Projekt, und wählen Sie dann **veröffentlichen**.
2. Neben der **Zielprofil** Liste der **Profil speichern** klicken Sie gemäß der folgenden Abbildung dargestellt. Dadurch wird ein Profil für Sie erstellt.
   
    ![Erstellen eines neuen Profils](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Wählen Sie nach dem Erstellen des Profils, **< verwalten… >** in die **Zielprofil** Liste.
   
    Die **Profile verwalten** Dialogfeld wird angezeigt, wie die folgende Abbildung zeigt.
   
    ![Profile-Dialogfeld "verwalten"](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. In der **Namen** aus, wählen Sie ein Profil aus, und wählen Sie dann **Kopie erstellen**.
5. Wählen Sie die **schließen** Schaltfläche.
   
    Das neue Profil wird in der Liste Zielprofil.
6. In der **Zielprofil** wählen Sie das Profil, das Sie gerade erstellt haben. Die Einstellungen des Veröffentlichungs-Assistenten werden mit den Optionen aus dem Profil gefüllt, die Sie ausgewählt haben.
7. Wählen Sie die **zurück** und **Weiter** Schaltflächen, um die einzelnen Seiten des Veröffentlichungs-Assistenten anzuzeigen, und passen Sie die Einstellungen für dieses Profil. Finden Sie unter [Assistent zum Veröffentlichen eines Azure-Anwendungen](http://go.microsoft.com/fwlink/p/?LinkID=623085) Informationen.
8. Nachdem Sie das Anpassen der Einstellungen fertig sind, wählen Sie **Weiter** um zurück zur Einstellungsseite zu wechseln. Das Profil wird gespeichert, wenn Sie den Dienst mit diesen Einstellungen veröffentlichen oder bei Auswahl von **speichern** neben der Liste der Profile.

### <a name="to-rename-or-delete-a-profile"></a>Umbenennen oder Löschen eines Profils
1. Öffnen Sie das Kontextmenü für Ihr Azure-Projekt, und wählen Sie dann **veröffentlichen**.
2. In der **Zielprofil** Liste **verwalten**.
3. In der **Profile verwalten** (Dialogfeld), wählen Sie das Profil, das Sie löschen möchten, und wählen Sie dann **entfernen**.
4. Wählen Sie im Dialogfeld zur Bestätigung, die angezeigt wird, **OK**.
5. Wählen Sie **schließen**.

### <a name="to-change-a-profile"></a>Um ein Profil zu ändern.
1. Öffnen Sie das Kontextmenü für Ihr Azure-Projekt, und wählen Sie dann **veröffentlichen**.
2. In der **Zielprofil** wählen Sie das Profil, das Sie ändern möchten.
3. Wählen Sie die **zurück** und **Weiter** Schaltflächen, um die einzelnen Seiten des Veröffentlichungs-Assistenten anzuzeigen, und klicken Sie dann ändern Sie die gewünschten Einstellungen. Finden Sie unter [Assistent zum Veröffentlichen eines Azure-Anwendungen](http://go.microsoft.com/fwlink/p/?LinkID=623085) Informationen.
4. Nachdem Sie das Ändern der Einstellungen fertig sind, wählen Sie **Weiter** zum zurückkehren der **Einstellungen** Seite.
5. (Optional) wählen **veröffentlichen** um den Cloud-Dienst mithilfe der neuen Einstellungen zu veröffentlichen. Wenn Sie nicht, Cloud-Dienst zu diesem Zeitpunkt veröffentlicht möchten und den Veröffentlichungs-Assistenten schließen, fragt Visual Studio Sie, wenn Sie die Änderungen am Profil speichern möchten.

## <a name="next-steps"></a>Nächste Schritte
Zum Konfigurieren anderer Teile des Azure-Projekts in Visual Studio finden Sie unter [Konfigurieren eines Azure-Projekts](http://go.microsoft.com/fwlink/p/?LinkID=623075)

