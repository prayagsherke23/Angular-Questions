1.Difference between subjects and Observable
-------------------------------------------------
<app-top-bar></app-top-bar>

<div class="container">
<button (click)="getObservable()">Get Observable</button>
<button (click)="getSubject()">Get Subject</button>
{{observableData1}} |{{observableData2}}
{{subjectData1}} | {{subjectData2}}
  <router-outlet></router-outlet>
</div>

-------------------------------------------------

import { Component } from '@angular/core';
import { Observable, Subject } from 'rxjs';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  subjectData='';
  observableData='';

  getObservable(){
    let myObservable = new Observable<string>(observer => {
      observer.next('Please Data Observer')
    });
    myObservable.subscribe(data=>{
      this.observableData = data
    })
  }

  getSubject(){
    let mySubject = new Subject<string>();

    mySubject.subscribe((data1: string) => {
      this.subjectData = data1;
    });
    mySubject.next('Please Data Subject'); 
  }
}

----------------------------------------------------

import { Component } from '@angular/core';
import { Observable, Subject } from 'rxjs';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  subjectData1='';
  subjectData2='';
  observableData1='';
  observableData2='';

  getObservable(){
    let myObservable = new Observable<any>(observer => {
      // observer.next('Please Data Observer')
      console.log(Math.ceil(Math.random()*100))
      observer.next(Math.floor(Math.random()*99)+1)
    });
    myObservable.subscribe(data=>{
      this.observableData1 = data
    })
    myObservable.subscribe(data=>{
      this.observableData2 = data
    })
  }

  getSubject(){
    let mySubject = new Subject<any>();

    mySubject.subscribe((data: any) => {
      this.subjectData1 = data;
    });
    mySubject.subscribe((data: any) => {
      this.subjectData2 = data;
    });
    // mySubject.next('Please Data Subject'); 
    mySubject.next(Math.floor(Math.random()*99)+1); 
  }
}=-[
