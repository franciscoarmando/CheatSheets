
```
<html>
       <form #form="ngForm" autocomplete="off" (submit)="OnSubmit(form)">
              <div class="form-group">
              <label>Id</label>
              <input class="form-control" 
                     placeholder="id" 
                     #id="ngModel" 
                     [(ngModel)]="service.id"
                     name="id">
              </div>
              <div class="form-group">
                     <label>Title</label>
                     <input class="form-control" 
                            placeholder="Title" 
                            #title="ngModel" 
                            [(ngModel)]="service.title"
                            name="title">
                     </div>
                     <div class="form-group">
                     <label>Duedate</label>
                     <input class="form-control" 
                            placeholder="Duedate" 
                            #duedate="ngModel" 
                            [(ngModel)]="service.duedate"
                            name="duedate">
                     </div>
                     <div class="form-group">
                            <label>Status</label>
                            <input class="form-control" 
                                   placeholder="Status" 
                                   #mstatus="ngModel" 
                                   [(ngModel)]="service.mstatus"
                                   name="mstatus">
                            </div>
                            <div class="form-group">
                            <button class="btn btn-primary form-control" name="BtnSave">Save</button>
                            </div>
              </form>
       </html>
```