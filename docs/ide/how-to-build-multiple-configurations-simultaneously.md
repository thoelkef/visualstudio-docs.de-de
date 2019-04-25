---
title: 'Vorgehensweise: Gleichzeitiges Erstellen mehrerer Konfigurationen'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac8d27397c6e4748546e21baf84abd7578ce8762
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547797"
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Vorgehensweise: Gleichzeitiges Erstellen mehrerer Konfigurationen

Über das Dialogfeld **Batch erstellen** können Sie die meisten Projekttypen mit mehreren oder allen Buildkonfigurationen gleichzeitig erstellen. Die folgenden Projekttypen können Sie jedoch nicht gleichzeitig in mehreren Buildkonfigurationen erstellen:

1. Für Windows erstellte [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps mit JavaScript.

2. Für Visual Basic-Projekte.

   Weitere Informationen zu Buildkonfigurationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

## <a name="to-build-a-project-in-multiple-build-configurations"></a>Erstellen eines Projekts in mehreren Buildkonfigurationen

1. Klicken Sie in der Menüleiste auf **Erstellen** > **Batch erstellen**.

2. Aktivieren Sie in der Spalte **Erstellen** die Kontrollkästchen für die Konfigurationen, in denen Sie ein Projekt erstellen möchten.

    > [!TIP]
    > Klicken Sie zum Bearbeiten oder Erstellen einer Buildkonfiguration für eine Projektmappe in der Menüleiste auf **Erstellen** > **Konfigurations-Manager**, um das Dialogfeld **Konfigurations-Manager** zu öffnen. Nachdem Sie eine Buildkonfiguration für eine Projektmappe bearbeitet haben, klicken Sie im Dialogfeld **Batch erstellen** auf die Schaltfläche **Neu erstellen**, um alle Buildkonfigurationen für die Projekte in der Projektmappe zu aktualisieren.

3. Klicken Sie auf **Erstellen** oder **Neu erstellen**, um das Projekt mit den von Ihnen angegebenen Konfigurationen zu erstellen.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)
- [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)
- [Paralleles Erstellen von mehreren Projekten](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)