# ButterKnife

1. in Activity  
```java
	protected void onCreate(Bundle savedInstanceState) {  
		super.onCreate(savedInstanceState);  
		setContentView(R.layout.activity_main);  
		ButterKnife.bind(this);  
	}  
```
2. in Fragment  
```java
	public class FancyFragment extends Fragment {  
		@BindView(R.id.button1)  
		Button button1;  
		@BindView(R.id.button2)  
		Button button2;  
  
		@Override   
		public View onCreateView(LayoutInflater inflater,  
								ViewGroup container,  
								Bundle savedInstanceState) {  
			View view = inflater.inflate(R.layout.fancy_fragment, container, false);  
			ButterKnife.bind(this, view);  
			return view;  
		}  
	}  
```
   
3. in ViewHolder  
```java
	public class MyAdapter extends BaseAdapter {  
		@Override  
		public View getView(int position, View view, ViewGroup parent) {  
			ViewHolder holder;  
			if (view != null) {  
        		holder = (ViewHolder) view.getTag();  
			} else {  
				view = inflater.inflate(R.layout.whatever, parent, false);  
				holder = new ViewHolder(view);  
				view.setTag(holder);  
			}  
			holder.name.setText("John Doe");  
			// etc...   
			return view;  
		}  
  
		static class ViewHolder {  
			@BindView(R.id.title)  
			TextView name;  
			@BindView(R.id.job_title)  
			TextView jobTitle;  
			public ViewHolder(View view) {  
        		ButterKnife.bind(this, view);  // ViewHoder를 초기화하면서 bind 해준다  
			}  
		}  
	}  
```
