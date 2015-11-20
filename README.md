# React Native Make Review Modal Component

> A React Native component for displaying a modal for making reviews. Compatible with both iOS and Android.

## Table of Contents

1. [Usage](#usage)
1. [Requirements](#requirements)
1. [Development](#development)
    1. [Installing Dependencies](#installing-dependencies)
    1. [Running the Scraper](#running-the-scraper)
    1. [Handling UCI Data Changes](#handling-uci-data-changes)
    1. [Roadmap](#roadmap)
1. [Contributing](#contributing)

## Usage

Install the package via `npm install react-native-make-review-modal --save`. Then require it in your JavaScript file via `require('react-native-make-review-modal')`. Check out an example usage below:

```js
var StarRating = require('react-native-star-rating');

if (Platform.OS === 'android'){
  var Portal = require('react-native/Libraries/Portal/Portal');
  var tag;
}

var ExampleComponent = React.createClass({
  getInitialState: function () {
    return {
      isReviewModalOpen: false,
    };
  },
  componentWillMount: function() {
    if( Platform.OS === 'android' ) {
      tag = Portal.allocateTag();
    }
  },
  onMakeReviewButtonPress: function () {
    if (Platform.OS === 'android') {
      Portal.showModal(tag, <MakeReviewModalView
        visible={this.state.isReviewModalOpen}
        isOpen={this.state.isReviewModalOpen}
        onSubmitReview={this.submitReview}
        onCloseReviewButtonPress={this.onCloseReviewButtonPress}
        titleText={'Test Modal'}
      />);
    }
    if (Platform.OS === 'ios') {
      this.setState({isReviewModalOpen: true});
    }
  },
  onCloseReviewButtonPress: function () {
    if (Platform.OS === 'android') {
      Portal.closeModal(tag);
    }
    if (Platform.OS === 'ios') {
      this.setState({isReviewModalOpen: false});
    }
  },
  submitReview: function (rating, review) {
    console.log('Submitting rating:' + rating + ', and review:' + review);
    this.onCloseReviewButtonPress();
  },
  render() {
    return (
      <MakeReviewModalView
        visible={this.state.isReviewModalOpen}
        isOpen={this.state.isReviewModalOpen}
        onSubmitReview={this.submitReview}
        onCloseReviewButtonPress={this.onCloseReviewButtonPress}
        titleText={'Test Modal'}
      />
    );
  }
});

module.exports = ExampleComponent;
```

## Requirements

- Node

## Development

### Installation

```sh
npm install react-native-make-review-modal --save
```

### Roadmap

View the project roadmap [here](https://github.com/djchie/react-native-make-review-modal/issues)

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.