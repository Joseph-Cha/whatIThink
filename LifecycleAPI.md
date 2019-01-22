###01/22<br>
<br>
##Lifecycle function<br>
<br>
#componentDidMount<br>
<br>
<br>
<br>
#componentWillReceiveProps<br>
-Called when the component may be receiving new props.<br>
React may call this even if porps have not changed,<br>
so be sure to compare new and exising props if you only want to handle changes.<br>
Calling 'component#setState generally does not trigger this method.<br>
<br>
componentWillReceiveProps는 새로운 props를 받게 되는 경우<br>
현재의 props와 새로운 props가 있어서 변화하는 부분을 알 수 있다.<br>
*새로운 props를 받기 전의 props가 this.props*이고, 새로 받게 될 props는 nextProps이다.<br>
따라서 -업데이트 되기 전의 API가 조회-될 것이다.
ex>
componentWillReceiveProps(nextProps){
console.log('current: ', this.props.selectedEvent);
console.log('next: ', nextProps.selectedEvent);
} 
이 경우 브라우저에서 버튼을 클릭하면 현재의 이벤트와 다음에 나올 이벤트를 콘솔창에서 확인할 수 있다.
('GithubImg/20190122_1.png') 
