# <a name="view-recent-job-performance-and-details"></a>Anzeigen aktueller Auftragsergebnisse und Details
Sobald die Aufträge übermittelt wurden, können Sie die Liste der Aufträge einsehen, um deren Status, Dauer und vieles mehr anzuzeigen.

1. Erweitern Sie im **Server-Explorer** den bestimmten Computekontext. 
1. Doppelklicken Sie auf **Aufträge**.
1. Die Liste der an diesen Computekontext übermittelten Aufträge wird angezeigt. 
1. Wählen Sie einen bestimmten **Auftrag** in der Liste aus, um Details anzuzeigen.

![Überwachen von Aufträgen](media\job-details\monitor-jobs.png)

> Der an Linux-VMs übermittelte Auftragsverlauf wird auf der VM im Verzeichnis „/tmp“ gespeichert. Daher wird bei jedem Neustart der Auftragsverlauf gelöscht. Für eine permanente Aufzeichnung Ihres Auftragsverlaufs konfigurieren Sie Ihre VM als Computekontext in Azure Machine Learning, und bermitteln Sie dann den Auftrag an Azure Machine Learning (wählen Sie dabei Ihre VM als Computekontext aus).