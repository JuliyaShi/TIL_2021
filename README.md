# TIL_2021
TIL_2021.md

Props and State are the two types of data that control a component.

- The simple rule of thumb is props should not be changed. In the programming world we call it “Immutable” or in simple english “Unchangeable”.
Components receive props from their parent. These props should not be modified inside the component. In React and React Native the data flows in one direction -> From the parent to the child.

// Parent 
export default class ScreenOne extends React.Component {
  render () {
    return (
     <View>
     	 <Heading message={'Custom Heading for Screen One'}/>
     </View>
    )
  }
}

// Child component
export default class Heading extends React.Component {
  render () {
    return (
      <View>
        <Text>{this.props.message}</Text>
      </View>
    )
  }
}
Heading.propTypes = {
  message: PropTypes.string
}
Heading.defaultProps = {
  message: 'Heading One'
}

In the example above we have a Heading component, with a message prop. The parent class ScreenOne sends the prop to the child component Heading.
Notice that the same component Heading can be reused several times with different message prop values passed to it from different parents components. The key here is to remember that the prop should not be modified inside the Heading component.

State
- State works differently when compared to props. State is internal to a component, while props are passed to a component.
- State can Change — Mutable

In english the ‘state of a being’ refers to the physical condition of a person, and it is a mere state, which changes over time. Well, similarly state in React/React Native is used within components to keep track of information.
Keep in mind not to update state directly using this.state. Always use setState to update the state objects. Using setState re-renders the component and all the child components. This is great, because you don’t have to worry about writing event handlers like other languages.
State is internal to a component, while props are passed to a component. In english the 'state of a being' refers to the physical condition of a person, and it is a mere state, which changes over time. Well, similarly state in React/React Native is used within components to keep track of information.
(https://codeburst.io/props-and-state-in-react-native-explained-in-simple-english-8ea73b1d224e)

Separate Hooks for Separate Effects

When multiple values are closely related and change at the same time, it can make sense to group these values in a collection like an object or array. Packaging data together can also add complexity to the code responsible for managing that data. Therefore, it is a good idea to separate concerns by managing different data with different Hooks.
