---
title: 'Vorgehensweise: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ab9204513c59d2c853c0a3738ef2363739d56c1
ms.sourcegitcommit: 551f13774e8bb0eb47cbd973745628a956e866aa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459620"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Gewusst wie: Deaktivieren der URL-Aktivierung von ClickOnce-Anwendungen

In der Regel wird eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Anwendung automatisch gestartet, sobald sie von einem Webserver installiert wurde. Aus Gründen der Sicherheit könnten Sie dieses Verhalten deaktivieren, und informieren Benutzer zum Starten der Anwendung aus der **starten** Menü stattdessen. Das folgende Verfahren beschreibt das Deaktivieren der URL-Aktivierung.

Dieses Verfahren kann nur für [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendungen verwendet werden, die von einem Webserver auf dem Computer des Benutzers installiert werden. Es kann nicht für reine Onlineanwendungen verwendet werden, die nur über ihre URL gestartet werden können. Weitere Informationen zu den Unterschieden zwischen reinen onlineanwendungen und installierten Anwendungen finden Sie unter [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md).

Diese Prozedur verwendet das Windows Software Development Kit (SDK) Tool MageUI.exe. Weitere Informationen zu diesem Tool finden Sie unter [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Sie können auch dieses Verfahren mithilfe von Visual Studio ausführen.

## <a name="procedure"></a>Prozedur

### <a name="to-disable-url-activation-for-your-application"></a>So deaktivieren Sie die URL-Aktivierung für Ihre Anwendung

1.  Öffnen Sie Ihr Bereitstellungsmanifest in „MageUI.exe“. Wenn Sie noch kein Manifest erstellt haben, führen Sie die Schritte in [Exemplarische Vorgehensweise: Manuelles bereitstellen eine ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2.  Wählen Sie die **Bereitstellungsoptionen** Registerkarte.

3.  Deaktivieren der **Anwendung nach dem Installieren automatisch ausführen** Kontrollkästchen.

4.  Speichern und signieren Sie das Manifest.

## <a name="see-also"></a>Siehe auch

- [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)