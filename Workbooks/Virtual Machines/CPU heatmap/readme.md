# <a name="cpu-heatmap"></a><span data-ttu-id="b9046-101">Mapa cieplna procesora CPU</span><span class="sxs-lookup"><span data-stu-id="b9046-101">CPU heatmap</span></span>

<span data-ttu-id="b9046-102">Ten skoroszyt jest dobrym sposobem wizualizacji punktów aktywnych wykorzystania procesora CPU maszyn wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="b9046-102">This workbook is a good way to visualize hot spots in the CPU utilization of your virtual machines.</span></span>

![Obraz mapy cieplnej procesora CPU](cpu-heatmap.png)

## <a name="changing-the-cpu-threshold"></a><span data-ttu-id="b9046-104">Zmiana progu procesora CPU</span><span class="sxs-lookup"><span data-stu-id="b9046-104">Changing the CPU threshold</span></span>
<span data-ttu-id="b9046-105">Domyślnie w tym skoroszycie są wyróżniane maszyny wirtualne ze średnią wartością `Percentage CPU` większą niż 75%.</span><span class="sxs-lookup"><span data-stu-id="b9046-105">By default, this workbook highlights virtual machines with average `Percentage CPU` greater than 75%.</span></span> <span data-ttu-id="b9046-106">Jeśli chcesz ustawić ten próg na niższą lub wyższą wartość, wykonaj poniższe kroki:</span><span class="sxs-lookup"><span data-stu-id="b9046-106">If you wish for this threshold to be higher or lower, these are the steps for follow:</span></span>

1. <span data-ttu-id="b9046-107">Kliknij element `Edit` na pasku narzędzi.</span><span class="sxs-lookup"><span data-stu-id="b9046-107">Click the `Edit` item in the toolbar.</span></span>
2. <span data-ttu-id="b9046-108">Kliknij przycisk `↑ Edit` w prawym dolnym obszarze kontrolki programu hive.</span><span class="sxs-lookup"><span data-stu-id="b9046-108">Click on the `↑ Edit` button to the bottom-right of the hive control.</span></span>
3. <span data-ttu-id="b9046-109">Na liście `Columns Available After Merge` przewiń w dół i wybierz element `[Added column] - Cell Color`.</span><span class="sxs-lookup"><span data-stu-id="b9046-109">In the `Columns Available After Merge` list, scroll down and select the `[Added column] - Cell Color` item.</span></span>
4. <span data-ttu-id="b9046-110">Kliknij przycisk `Edit added item` na pasku narzędzi kontrolek programu hive.</span><span class="sxs-lookup"><span data-stu-id="b9046-110">Click on the `Edit added item` button in the hive controls toolbar.</span></span>
5. <span data-ttu-id="b9046-111">W wyświetlonym okienku kliknij pozycję `Edit` dla elementu `Percentage CPU > 75 Result is E8976A`, aby wyświetlić okno podręczne ustawień</span><span class="sxs-lookup"><span data-stu-id="b9046-111">In the pane tha opens up, click `Edit` on the item that says `Percentage CPU > 75 Result is E8976A` to see a settings pop up</span></span>
    1. <span data-ttu-id="b9046-112">W polu `Second operand` ustaw żądaną wartość progu — na przykład 90.</span><span class="sxs-lookup"><span data-stu-id="b9046-112">Set the `Second operand` field to the threshold you want - say 90.</span></span>
        <span data-ttu-id="b9046-113">![Obraz mapy cieplnej procesora CPU](cpu-heatmap-column-settings.png)</span><span class="sxs-lookup"><span data-stu-id="b9046-113">![Image a CPU heatmap](cpu-heatmap-column-settings.png)</span></span>
    2. <span data-ttu-id="b9046-114">Kliknij opcję w menu podręcznym.</span><span class="sxs-lookup"><span data-stu-id="b9046-114">Click op in the popup.</span></span>
6. <span data-ttu-id="b9046-115">Kliknij pozycję „Zapisz i zamknij”</span><span class="sxs-lookup"><span data-stu-id="b9046-115">Click 'Save and close'</span></span>
7. <span data-ttu-id="b9046-116">Wybierz pozycję `Done Editing` na pasku narzędzi skoroszytu.</span><span class="sxs-lookup"><span data-stu-id="b9046-116">Choose `Done Editing` in the workbook toolbar.</span></span>
