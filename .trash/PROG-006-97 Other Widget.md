```dart title: Show caregiver id in a SnackBar when the page first appears (if present)
    WidgetsBinding.instance.addPostFrameCallback((_) {
      final caregiverId = ref.read(caregiverIdProvider);
      if (caregiverId != null && caregiverId.isNotEmpty) {
      
        debugPrint(
          'Reached RegisterCareRecipientPage with caregiverId: $caregiverId',
        );
        ScaffoldMessenger.of(
          context,
        ).showSnackBar(SnackBar(content: Text('Caregiver id: $caregiverId')));
      }
    });
  }
```