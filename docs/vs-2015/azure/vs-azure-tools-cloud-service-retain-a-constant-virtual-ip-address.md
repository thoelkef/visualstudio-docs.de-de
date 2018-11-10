---
title: 'Gewusst wie: beibehalten eine Konstante virtuelle IP-Adresse für einen Azure-Cloud-Dienst | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie sicherstellen, dass die virtuelle IP-Adresse (VIP) des Azure-Cloud-Diensts nicht ändert.
author: ghogen
manager: douge
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e74cc5b9bbbfea92d2dea2c00ee5b0f98dc02f21
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001981"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Beibehalten einer konstanten virtuellen IP-Adresse für einen Azure-Clouddienst
Wenn Sie einen Cloud-Dienst, der in Azure gehostet wird aktualisieren, müssen Sie sicherstellen, dass die virtuelle IP-Adresse (VIP) des Diensts nicht ändert. Viele domänenverwaltungsdienste verwenden das Domain Name System (DNS) für die Registrierung der Domänennamen. DNS funktioniert nur, wenn die VIP unverändert bleibt. Sie können die **Veröffentlichungs-Assistenten** in Azure-Tools, um sicherzustellen, dass die VIP Ihres Clouddiensts, wenn nicht ändert, aktualisieren Sie es. Weitere Informationen zur Verwendung von DNS-domänenverwaltung für Cloud Services finden Sie unter [Konfigurieren eines benutzerdefinierten Domänennamens für einen Azure-Cloud-Dienst](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Veröffentlichen eines Clouddiensts, ohne die VIP zu ändern
Die VIP eines Clouddiensts wird zugeordnet, wenn Sie erstmalig in Azure in einer bestimmten Umgebung, z. B. der produktionsumgebung bereitgestellt wird. Die VIP ändert sich nur, wenn Sie die Bereitstellung explizit löschen oder die Bereitstellung durch den bereitstellungsaktualisierungsvorgang implizit gelöscht. Um die VIP beibehalten möchten, müssen Sie nicht die Bereitstellung löschen, und Sie müssen sicherstellen, dass Visual Studio die Bereitstellung nicht automatisch löscht. 

Sie können angeben, dass der bereitstellungseinstellungen in den **Veröffentlichungs-Assistenten**, unterstützt verschiedene Bereitstellungsoptionen. Sie können angeben, eine neue Bereitstellung oder eine updatebereitstellung, die inkrementell oder gleichzeitig erfolgen kann. Beide Arten von updatebereitstellungen wird die VIP beibehalten. Definitionen dieser verschiedenen Typen der Bereitstellung, finden Sie unter [Assistent zum Veröffentlichen eines Azure-Anwendungen](vs-azure-tools-publish-azure-application-wizard.md). Darüber hinaus können Sie steuern, ob die vorherige Bereitstellung eines Clouddiensts gelöscht wird, wenn ein Fehler auftritt. Wenn Sie diese Option nicht korrekt festlegen, wird die VIP möglicherweise unerwartet geändert.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Aktualisieren Sie ohne Änderung der VIP eines Clouddiensts
1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio. 

2. In **Projektmappen-Explorer**, mit der rechten Maustaste in des Projekts. Wählen Sie im Kontextmenü den Befehl **veröffentlichen**.

    ![Menü "Veröffentlichen"](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. In der **Azure-Anwendung veröffentlichen** Dialogfeld Feld, wählen Sie das Azure-Abonnement, das Sie bereitstellen möchten. Melden Sie sich, falls erforderlich, und wählen **Weiter**.

    ![Azure-Anwendung-Anmeldung Seite "Veröffentlichen"](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Auf der **Allgemeine Einstellungen** Registerkarte, stellen Sie sicher, die der Namen des Cloud-service, die Sie bereitstellen möchten, wird die **Umgebung**, wird die **Buildkonfiguration**, und die **Dienstkonfiguration** richtig sind.

    ![Veröffentlichen Sie die Registerkarte "Allgemeine Einstellungen für die Azure-Anwendung"](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Auf der **Erweiterte Einstellungen** Registerkarte, überprüfen Sie, ob die **bereitstellungsbezeichnung** und die **Speicherkonto** richtig sind. Überprüfen Sie, ob die **Bereitstellung bei Fehler löschen** das Kontrollkästchen deaktiviert ist, und überprüfen Sie, ob die **bereitstellungsaktualisierung** das Kontrollkästchen aktiviert ist. Durch Deaktivieren der **Bereitstellung bei Fehler löschen** Kontrollkästchen, Sie stellen Sie sicher, dass die VIP nicht verloren geht, wenn während der Bereitstellung ein Fehler auftritt. Durch Auswahl der **bereitstellungsaktualisierung** Kontrollkästchen, Sie stellen Sie sicher, dass die Bereitstellung nicht gelöscht, und die VIP nicht verloren, wenn Sie Ihre Anwendung erneut veröffentlichen. 

    ![Veröffentlichen Sie die Registerkarte "Azure-Anwendung Erweiterte Einstellungen"](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Um festzulegen, wie Sie die Rollen aktualisiert werden sollen, wählen Sie **Einstellungen** neben **bereitstellungsaktualisierung**. Wählen Sie entweder **inkrementelles Update** oder **gleichzeitige Aktualisierung**, und wählen Sie **OK**. Wählen Sie **inkrementelles Update** um jede Instanz Ihrer Anwendung nacheinander zu aktualisieren, damit die Anwendung immer verfügbar ist. Wählen Sie **gleichzeitige Aktualisierung** auf alle Instanzen der Anwendung gleichzeitig zu aktualisieren. Gleichzeitige Updates sind schneller, aber Ihr Dienst möglicherweise nicht zur Verfügung während des Updates. Wenn Sie fertig sind, wählen Sie **Weiter**.

    ![Einstellungen für Azure-Anwendung zur Seite "Veröffentlichen"](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. In der **Azure-Anwendung veröffentlichen** wählen Sie im Dialogfeld **Weiter** erst die **Zusammenfassung** angezeigt wird. Überprüfen Sie die Einstellungen, und wählen Sie dann **veröffentlichen**.
   
    ![Zusammenfassung der Azure-Anwendung-Seite "Veröffentlichen"](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Nächste Schritte
- [Mithilfe des Visual Studio-Webpublishing-Assistenten der Azure-Anwendung](vs-azure-tools-publish-azure-application-wizard.md)

