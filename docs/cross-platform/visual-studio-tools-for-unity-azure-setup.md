---
title: "Visual Studio-Tools für Unity: Einrichtung – Exemplarische Vorgehensweise für Azure | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: FFE17FC6-0B47-4A00-A125-01BD49E3873C
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 447f32c2e736084a08223b56f4188ca7c8abeea5
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="create-easy-tables"></a>Erstellen einfacher Tabellen

Da Sie nun über eine mobile App in Azure mit initialisierten einfachen Tabellen verfügen, ist es an der Zeit, die Tabellen zu erstellen, in denen die von einem Unity-Spiel übermittelten Daten nachverfolgt werden können.

## <a name="setup-the-crash-heatmap-table"></a>Einrichten der Absturzwärmebildtabelle

1. Klicken Sie im Azure-Portal auf „Alle Ressourcen“, und wählen Sie dann die mobile App aus, für die Sie „Einfache Tabellen“ in den vorherigen Schritten konfiguriert haben.

  ![Auswählen der mobilen App](media/vstu_azure-setup-table-schema-image1.png)

2. Scrollen Sie nach unten zur Überschrift **MOBILE** (MOBIL), und wählen Sie **Einfache Tabellen** aus. Es sollte keine Nachricht mehr über die Initialisierung Ihrer App für „Einfache Tabellen“ angezeigt werden  

  ![Auswählen von „Einfachen Tabellen“](media/vstu_azure-setup-table-schema-image2.png)

3. Klicken Sie auf die Schaltfläche **Hinzufügen**.

  ![Klicken auf „Hinzufügen“](media/vstu_azure-setup-table-schema-image3.png)

4. Nennen Sie die Tabelle **CrashInfo**, und klicken Sie auf **OK**. Behalten Sie für die übrigen Optionen die Standardeinstellungen bei.

  > [!WARNING]
  > Dieser Name muss mit dem Namen der Datenmodellklasse übereinstimmen, die später in dieser exemplarischen Vorgehensweise erstellt wird.

  ![Eingeben eines Namens und Klicken auf OK](media/vstu_azure-setup-table-schema-image4.png)

5. Sie werden benachrichtigt, wenn die neue Tabelle erstellt wurde.

> [!NOTE]
> Mithilfe von „Einfache Tabellen“ wird das Tabellenschema tatsächlich dynamisch erstellt, da Daten hinzugefügt werden. Das bedeutet, dass geeignete Datenspalten während dieses Schritts nicht manuell eingerichtet werden müssen.

## <a name="setup-the-leaderboard-table"></a>Einrichten der Bestenlistentabelle

1. Wechseln Sie zurück zum Blatt „Einfache Tabellen“, und klicken Sie auf **Hinzufügen**, um eine zweite Tabelle hinzuzufügen.

  ![Hinzufügen einer zweiten Tabelle](media/vstu_azure-setup-table-schema-image10.png)

2. Nennen Sie die neue Tabelle **HighScoreInfo**, und klicken Sie auf **OK**. Behalten Sie für die übrigen Optionen die Standardeinstellungen bei.

  > [!WARNING]
  > Dieser Name muss mit dem Namen der Datenmodellklasse übereinstimmen, die später in dieser exemplarischen Vorgehensweise erstellt wird.

  ![Eingeben eines Namens und Klicken auf OK](media/vstu_azure-setup-table-schema-image11.png)

3. Sie werden benachrichtigt, wenn die neue Tabelle erstellt wurde.


## <a name="next-step"></a>Nächster Schritt

* [Vorbereiten der Entwicklungsumgebung](visual-studio-tools-for-unity-azure-prepare.md)
