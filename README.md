Get no of records selected by checkbox for send for approval from WORKFLOW_RUNS table having the column ITEMS FOR APPROVAL and return the result in number integer @GetMapping(" /getNoOfRecordsSubmited”} write controler service repo for this in java spring @RestController
public class WorkflowRunsController {
    
    @Autowired
    private WorkflowRunsService workflowRunsService;

    @GetMapping("/getNoOfRecordsSubmitted")
    public long getNoOfRecordsSubmitted(@RequestParam boolean itemsForApproval) {
        return workflowRunsService.getNoOfRecordsSubmitted(itemsForApproval);
    }
}public long getNoOfRecordsSubmitted(boolean itemsForApproval) {
        return workflowRunsRepository.countByItemsForApproval(itemsForApproval);
    } public interface WorkflowRunsRepository extends JpaRepository<WorkflowRuns, Long> {
    
    @Query("SELECT COUNT(wr) FROM WorkflowRuns wr WHERE wr.itemsForApproval = :itemsForApproval")
    long countByItemsForApproval(@Param("itemsForApproval") boolean itemsForApproval);
}
