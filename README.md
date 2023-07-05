# COMP229-M2023-Midterm-301249275

HOI KIT FAN
STUDENT ID: 301249275
07-15-2023

<div *ngIf="viewMode; else editable">
  <div *ngIf="currentProduct.id">
    <h4>Product</h4>
    <div>
      <label><strong>Name:</strong></label> {{ currentProduct.name }}
    </div>
    <div>
      <label><strong>Description:</strong></label>
      {{ currentProduct.description }}
    </div>
    <div>
      <label><strong>Status:</strong></label>
      {{ currentProduct.published ? "Published" : "Pending" }}
    </div>

    <button class="badge badge-primary" (click)="editModeOn()">
      Edit
    </button>

  </div>

  <div *ngIf="!currentProduct">
    <br />
    <p>Please click on a Product...</p>
  </div>
</div>

<ng-template #editable>

  <div *ngIf="currentProduct.id" class="edit-form">
    <h4>Product</h4>
    <form>
      <div class="form-group">
        <label for="title">Name</label>
        <input
          type="text"
          class="form-control"
          id="name"
          [(ngModel)]="currentProduct.name"
          name="name"
        />
      </div>

      <div class="form-group">
        <label for="description">Description</label>
        <input
          type="text"
          class="form-control"
          id="description"
          [(ngModel)]="currentProduct.description"
          name="description"
        />
      </div>

      <div class="form-group">
        <label><strong>Status:</strong></label>
        {{ currentProduct.published ? "Published" : "Pending" }}
      </div>
    </form>

    <button
      class="badge badge-primary mr-2"
      *ngIf="currentProduct.published"
      (click)="updatePublished(false)"
    >
      Unpublish
    </button>

    <button
      *ngIf="!currentProduct.published"
      class="badge badge-primary mr-2"
      (click)="updatePublished(true)"
    >
      Publish
    </button>

    <button class="badge badge-danger mr-2" (click)="deleteProduct()">
      Delete
    </button>

    <button
      type="submit"
      class="badge badge-success"
      (click)="updateProduct()"
    >
      Update
    </button>

    <p>{{ message }}</p>

  </div>

  <div *ngIf="!currentProduct.id">
    <br />
    <p>Cannot access this Product...</p>
  </div>
</ng-template>
