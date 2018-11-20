# react-tabs
Simple React tabs menu

<script crossorigin src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>

<div id="root">
    
</div>

```jsx
class HelloMessage extends React.Component {
  render() {
    return <div>Hello {this.props.name}</div>;
  }
}

ReactDOM.render(
  <HelloMessage name="Taylor" />,
  document.getElementById('root')
);
```
 var data = [
  {id : '1',
   tabTitle: "Tab 1",
   tabContent: 'Tab Content'
  },
  {id : '2',
   tabTitle: "Tab 2",
   tabContent: 'Tab Content 2'
  },
  {id : '3',
   tabTitle: "Tab 3",
   tabContent: 'Tab Content 3'
  }
]

function TabTitle(props){
  return(
    props.isActive === props.dataTab
    ? <li onClick={props.onClick} className="tab-title tab-title--active" data-tab={props.dataTab}>{props.title}</li>
    : <li onClick={props.onClick} className="tab-title" data-tab={props.dataTab}>{props.title}</li>
  )
}

function TabContent(props){
  return(
    <p style={props.style} data-tab={props.dataTab}>{props.content}</p>
  )
}

class Tabs extends React.Component {
  constructor(props) {
      super(props);
      this.state = {isActive: '1'};
      this.changeActive = this.changeActive.bind(this)
  }
  
  changeActive(ev){
    this.setState({isActive: ev.target.getAttribute("data-tab")})
  }
  
  render(){
    var listTitle = this.props.data.map((item) => 
      <TabTitle isActive={this.state.isActive} onClick={this.changeActive} dataTab={item.id} title={item.tabTitle} />
    )                                        
     var listContent = this.props.data.map((item) => 
          this.state.isActive === item.id 
          ? <TabContent dataTab={item.id} content={item.tabContent} />
          : <TabContent style={{display: 'none'}} dataTab={item.id} content={item.tabContent} />
      )
    return(
      <div className="tabs">
        <ul className="tabs-titles">
          {listTitle}
        </ul>
        <div className="tab-content">
           {listContent}
        </div>
      </div>
    )
  }
}
    
    
ReactDOM.render(
  <Tabs data={data}/>,
  document.getElementById('root')
)
</script>
